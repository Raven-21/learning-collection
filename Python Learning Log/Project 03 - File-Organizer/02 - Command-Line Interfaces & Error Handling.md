# Command-Line Interfaces & Error Handling

After adding logging and basic file-system safety, I continued improving the way a Python program can interact with users from the command line.

Until this point, most of my programs had relied on either hard-coded values or `input()`.

For example, a value might be written directly into the program:

```python
organizer = Organizer("test_folder")
```

or requested after the program had already started:

```python
name = input("Enter a name: ")
```

This stage introduced a different approach: **command-line arguments**.

Instead of starting the program first and then waiting for input, information can be passed to the program when it is launched.

For example:

```bash
python main.py test_folder
```

Here, `test_folder` is passed to the program before its main logic begins.

## Using `argparse`

Python provides the built-in `argparse` module for parsing command-line arguments.

```python
import argparse
```

A parser can be created with:

```python
parser = argparse.ArgumentParser(
    description="Organize files in a folder by file type."
)
```

The parser defines what arguments the program accepts and can also automatically generate help and error messages.

## Defining Arguments with `add_argument()`

Arguments are registered with:

```python
parser.add_argument(...)
```

For example:

```python
parser.add_argument(
    "folder",
    help="Path to the folder to organize."
)
```

Because `folder` does not begin with `-` or `--`, it is a **positional argument**.

That means a value must be supplied in the expected position:

```bash
python main.py test_folder
```

The program interprets:

```text
test_folder
```

as the value of the `folder` argument.

## Parsing Arguments

Defining arguments is not enough by itself.

The program must then parse the actual command-line input:

```python
args = parser.parse_args()
```

After parsing, the values become available through the resulting `args` object.

For example:

```python
args.folder
```

may contain:

```text
test_folder
```

The overall process is:

```text
add_argument()
→ define what arguments are accepted

parse_args()
→ read the arguments supplied by the user

args.<name>
→ access the parsed value
```

## Positional and Optional Arguments

A command-line interface can contain different kinds of arguments.

A positional argument might look like:

```python
parser.add_argument("folder")
```

and be used as:

```bash
python main.py test_folder
```

An optional argument usually begins with `--`.

For example:

```python
parser.add_argument(
    "--dry-run",
    action="store_true",
    help="Show what would be moved without actually moving files."
)
```

It can then be used as:

```bash
python main.py test_folder --dry-run
```

The two arguments have different purposes:

```text
folder
→ positional argument
→ supplies a required value

--dry-run
→ optional argument
→ enables an additional behavior
```

## Boolean Flags with `store_true`

The option:

```python
action="store_true"
```

turns an argument into a Boolean switch.

Without the option:

```bash
python main.py test_folder
```

the result is:

```python
args.dry_run == False
```

With:

```bash
python main.py test_folder --dry-run
```

the result becomes:

```python
args.dry_run == True
```

This makes it possible for command-line arguments to control program behavior.

The command-line name:

```text
--dry-run
```

becomes:

```python
args.dry_run
```

inside Python because Python identifiers cannot contain hyphens.

## Command-Line Arguments vs `input()`

Command-line arguments and `input()` both allow users to provide data, but they happen at different stages.

With `input()`:

```text
Start program
→ program begins running
→ program asks a question
→ user enters a value
→ program continues
```

With command-line arguments:

```text
User writes command and arguments
→ program starts
→ arguments are parsed
→ program runs using those values
```

This makes command-line arguments especially useful for utility programs that can perform a task directly from a command.

## Dry-Run Mode

A useful command-line feature is **dry-run mode**.

A dry run means:

> Simulate an operation and report what would happen without actually modifying anything.

For example:

```bash
python main.py test_folder --dry-run
```

may produce:

```text
Would move: image.jpg -> Images
Would move: report.pdf -> Documents
```

while leaving the actual files unchanged.

This is especially useful when a program performs potentially destructive operations.

## Avoiding Side Effects During a Dry Run

A dry run should not only avoid moving files. It should avoid **all unnecessary modifications** to the system.

For example, this expression:

```python
destination = self.folder_path / category / file.name
```

only constructs a `Path` object representing a possible destination.

It does not create anything.

However:

```python
category_folder = self.create_category_folder(category)
```

may actually call `mkdir()` and create a directory.

Therefore, dry-run logic should calculate possible paths without performing operations such as:

```text
Creating directories
Moving files
Deleting files
Renaming files
Overwriting data
```

This helped reinforce an important distinction:

> Describing or calculating a future operation is different from actually performing that operation.

## Using Command-Line Values in Objects

Parsed arguments can be passed into normal Python functions or objects.

For example:

```python
organizer = Organizer(
    folder_path=args.folder,
    dry_run=args.dry_run
)
```

Here:

```python
args.folder
```

is the value parsed from the command line.

```python
folder_path=
```

specifies which constructor parameter should receive that value.

Likewise:

```python
dry_run=args.dry_run
```

means:

> Pass the parsed `dry_run` value into the `dry_run` parameter.

This also reinforced the difference between Python function-call syntax and command-line syntax.

In Python:

```text
positional arguments
vs
keyword arguments
```

are concepts related to function calls.

In a command-line interface:

```text
positional arguments
vs
optional arguments
```

are concepts defined by tools such as `argparse`.

The names are similar, but they describe different layers of the program.

## Improving Error Handling

Once a program accepts user-supplied paths, invalid input becomes unavoidable.

For example, a path may not exist:

```python
if not self.folder_path.exists():
    raise ValueError("Path does not exist.")
```

or it may refer to a file instead of a directory:

```python
if not self.folder_path.is_dir():
    raise ValueError("Path is not a folder.")
```

The class that detects the invalid state can raise an exception.

The program entry point can then decide how to communicate the problem to the user:

```python
try:
    organizer = Organizer(
        folder_path=args.folder,
        dry_run=args.dry_run
    )

    organizer.organize()

except ValueError as error:
    logging.error(error)
```

Instead of displaying a full Python traceback, the command-line user can receive a concise message such as:

```text
ERROR: Path does not exist.
```

This creates a useful separation of responsibilities:

```text
Lower-level code
→ detects the problem
→ raises an exception

Application entry point
→ catches the exception
→ presents the error to the user
```

## File Operation Errors

Even a valid path does not guarantee that every file operation will succeed.

Operations involving the operating system may fail because of:

* Permission restrictions
* Files being unavailable
* Invalid file-system states
* Device or operating-system errors

For this reason, file operations can also handle exceptions such as:

```python
PermissionError
```

and:

```python
OSError
```

For example:

```python
try:
    shutil.move(source, destination)

except PermissionError:
    logging.error("Permission denied.")

except OSError as error:
    logging.error(f"File operation failed: {error}")
```

`PermissionError` represents a more specific permission-related failure.

`OSError` represents a broader category of operating-system errors.

This also demonstrates an important exception-handling principle:

> Catch specific exceptions when a specific response is useful, while broader exceptions can handle more general failures.

## User-Friendly Errors vs Tracebacks

A traceback is extremely useful during development because it shows:

* Where an exception occurred
* Which functions were called
* The exception type
* The exception message

However, a normal user usually does not need all of that information.

A command-line application often benefits from converting internal exceptions into concise messages:

```text
ERROR: Path does not exist.
```

rather than exposing implementation details.

This does not mean exceptions are hidden or ignored.

Instead, the program handles them deliberately and presents information at the appropriate level.

## What I Learned

The main technical concepts from this stage include:

* `argparse`
* `ArgumentParser`
* `add_argument()`
* `parse_args()`
* Positional command-line arguments
* Optional command-line arguments
* `action="store_true"`
* Boolean CLI flags
* `args.folder`
* `args.dry_run`
* Dry-run behavior
* Avoiding side effects
* Keyword arguments in Python function calls
* CLI input versus `input()`
* `try` / `except`
* `ValueError`
* `PermissionError`
* `OSError`
* User-friendly error reporting with logging

More importantly, this stage introduced a different way of thinking about a program.

Previously, I mostly thought of a Python program as something I opened and interacted with after it started.

A command-line tool can instead be used almost like a command itself:

```bash
python main.py <target> [options]
```

The user specifies what should happen at launch, and the program performs the requested task.

I also became more aware of the boundary between internal program logic and the user interface.

The core logic should detect and report problems accurately, while the outer application layer decides how those problems should be presented.

Finally, dry-run mode introduced another important software-design principle:

> A safe tool should sometimes allow users to preview the consequences of an operation before making changes.

These ideas make a command-line program more predictable, safer, and easier to use.