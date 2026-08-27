# File Organizer v1.0

File Organizer was my third Python project and the first one that made me work directly with the operating system and the real file system.

Compared with my previous projects, this project felt more practical because the program was not only managing data inside Python. It had to scan real directories, inspect real files, create folders, move files, handle conflicts, and respond safely when something went wrong.

The basic idea was simple:

```text
Scan files
    ↓
Categorize files
    ↓
Create category folders
    ↓
Move files
```

However, as the project developed, I discovered that building a reliable file utility required much more than implementing this core workflow.

## Designing the Core Structure

The project was divided into a few clear modules.

`main.py` became responsible for:

* Command-line arguments
* Logging configuration
* Starting the program
* Handling user-facing errors

`organizer.py` contained the main file-management logic.

`config.py` stored file categories and ignored filenames.

This separation helped reinforce the idea that different parts of a program should have different responsibilities.

Instead of placing everything into one file, the project gradually became a small but structured application.

## Working with `pathlib`

One of the main new topics in this project was `pathlib`.

Instead of treating file paths only as strings, I began working with `Path` objects.

For example:

```python
self.folder_path = Path(folder_path)
```

This made file-system operations much clearer.

I used:

```python
Path.iterdir()
Path.is_file()
Path.exists()
Path.is_dir()
Path.name
Path.suffix
Path.mkdir()
```

I also learned that paths can be combined using `/`:

```python
destination = folder / category / file.name
```

This made path construction much easier to read than manually combining strings.

## Scanning and Categorizing Files

The program scans the target directory and collects files while ignoring directories.

```python
for item in self.folder_path.iterdir():
    if item.is_file():
        ...
```

Files are then categorized using their extensions.

```python
suffix = file.suffix.lower()
```

The extension is compared against category definitions stored in a dictionary.

This gave me more practice with:

* Dictionaries
* Lists
* `.items()`
* Membership testing with `in`
* String normalization with `.lower()`

Files that do not match any known category are placed into `Others`.

## Working with Real File-System Behavior

One unexpected discovery was `desktop.ini`.

Even when it was not visible in Windows Explorer, Python could still detect it through the file system.

This reminded me that:

> The actual state of the file system is not always the same as what a graphical interface chooses to display.

I added an ignored-file configuration so that system-related files could be skipped safely.

This was one of the first moments where the project clearly moved beyond simple programming exercises and started dealing with real operating-system behavior.

## Safe File Movement

Files are moved using `shutil.move()`.

Before moving a file, the program checks whether the destination already exists.

This prevents accidental overwriting.

Instead of treating every unsuccessful move in the same way, I eventually changed the return value of `move_file()` from a simple Boolean result into clearer status values.

For example:

```text
moved
dry-run
skipped
failed
```

This was an important design improvement.

A Boolean result such as:

```python
True
False
```

works well when there are only two meaningful outcomes.

But once a function can succeed, skip an operation, simulate an operation, or fail, a Boolean value becomes ambiguous.

This taught me that return values should communicate enough information for the calling code to understand what actually happened.

## Dry-Run Mode

One of the most useful features added during the project was:

```text
--dry-run
```

The program can now be run like:

```bash
python main.py target_folder --dry-run
```

Dry-run mode previews what would happen without actually changing the file system.

This required more careful thinking than simply avoiding `shutil.move()`.

For a true dry run, the program should also avoid creating directories or making any other changes.

I learned to distinguish between:

```python
destination = folder / category / file.name
```

which only constructs a possible path,

and:

```python
folder.mkdir()
```

which produces an actual side effect.

This introduced an important software-design idea:

> A preview mode should simulate the consequences of an operation without performing the operation itself.

## Building a Command-Line Interface

Before this project, I was more familiar with interactive input using:

```python
input()
```

This project introduced me to command-line arguments with `argparse`.

The target folder is provided as a positional argument:

```bash
python main.py target_folder
```

while `--dry-run` is an optional argument.

I learned about:

```python
ArgumentParser()
add_argument()
parse_args()
```

as well as:

```python
action="store_true"
```

I also learned the difference between two similar sets of concepts:

```text
Command-line interface:
positional arguments
optional arguments
```

and:

```text
Python function calls:
positional arguments
keyword arguments
```

These concepts have similar names but belong to different layers of the program.

Using the terminal also helped me understand that a Python program can behave like a command-line tool rather than only something launched through an IDE.

## Logging

Another major addition was Python's `logging` module.

At first, program results were displayed using:

```python
print()
```

Later, they were replaced with structured log messages.

For example:

```python
logging.info(...)
logging.warning(...)
logging.error(...)
```

I learned the difference between log levels and used handlers to send logs to both:

```text
Terminal
+
Log file
```

The program now keeps a persistent record of operations in:

```text
file_organizer.log
```

This helped me understand that logging is not simply a more complicated version of `print()`.

Its purpose is to create a structured and useful history of what a program did.

## Exception Handling

The project also gave me more realistic practice with exception handling.

The target path is validated before the program begins organizing files.

For example:

```python
if not self.folder_path.exists():
    raise ValueError("Path does not exist.")

if not self.folder_path.is_dir():
    raise ValueError("Path is not a folder.")
```

The program entry point catches these expected errors and presents them through logging instead of showing a full traceback to the user.

File operations also handle:

```python
PermissionError
OSError
```

This reinforced the separation between different responsibilities:

```text
Lower-level code
→ detects problems

Higher-level code
→ decides how to present them
```

I also learned that exception handling should not simply hide errors. It should make expected failures understandable while keeping unexpected problems visible enough to debug.

## The Program Entry Point

Near the end of the project, I reorganized `main.py` around:

```python
def main() -> None:
    ...
```

and:

```python
if __name__ == "__main__":
    main()
```

This structure separates direct program execution from module importing.

It also made `main.py` feel more like a proper application entry point rather than a script containing only top-level statements.

## Code Review and Refactoring

Before finishing v1.0, I reviewed the project structure instead of immediately adding more features.

One important issue discovered during the review was the ambiguous Boolean return value from `move_file()`.

The code worked, but the design did not clearly distinguish between:

* A file being skipped because it already existed
* A file operation failing
* A successful move
* A simulated dry-run operation

Refactoring this into explicit result states improved both readability and correctness.

This reminded me that code review is not only about finding syntax errors.

It is also about asking:

* Is the meaning of this code clear?
* Are responsibilities separated correctly?
* Can the program represent all of its possible states accurately?
* Is the design becoming more complicated than necessary?

## What Was Different from My Previous Projects

My first project mainly helped me move from basic Python syntax into functions, classes, exceptions, files, and modular design.

My second project gave me more experience with data models, CRUD operations, JSON persistence, and application structure.

File Organizer introduced a different layer:

```text
Python
    ↕
Operating System
    ↕
Real File System
```

The biggest new topics included:

* `pathlib`
* `shutil`
* File-system interaction
* System and hidden files
* File conflicts
* Safe operations
* `logging`
* Command-line interfaces
* `argparse`
* Dry-run behavior
* Operating-system exceptions

Because of this, the project felt more like building a real utility than only practicing Python language features.

## What I Learned Most

The most important lesson from this project was that software development is not only about making the main feature work.

A first version of a program may successfully perform:

```text
Scan → Categorize → Move
```

but real software also has to answer questions such as:

* What if the path is invalid?
* What if the destination already contains the file?
* What if the operating system refuses the operation?
* What if the user wants to preview the result first?
* How can the program explain what happened?
* How can past operations be inspected later?

These questions gradually changed the way I approached the project.

I started by asking:

> How can I make the program perform this task?

By the end, I was also asking:

> How can the program perform this task safely, clearly, and predictably in a real environment?

That change in thinking was probably the most valuable part of the project.

## Final Result

The v1.0 version now includes:

* File scanning
* Extension-based categorization
* Automatic category folder creation
* File movement
* Unknown-file handling
* Ignored-file rules
* Path validation
* File conflict protection
* Logging
* Command-line arguments
* Dry-run mode
* User-friendly error reporting
* File-operation exception handling
* A structured program entry point

File Organizer started as a simple automation idea, but it became a useful exercise in file-system programming, command-line application design, error handling, and software reliability.

It also marked another step in moving from learning individual Python features toward learning how those features work together inside a complete program.