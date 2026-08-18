# File System Safety & Logging


After finishing Guess the Number and To-Do List, I started my third Python project: **File Organizer**.

The biggest difference between this project and the previous two is that the program is no longer dealing only with its own internal data. It is now interacting directly with real files and directories in the operating system.

At this stage, File Organizer has completed its basic core workflow:

```text
Scan files
    ↓
Categorize files
    ↓
Create category folders
    ↓
Move files
```

At first, I was mainly focused on making the program organize files successfully. However, once the core functionality started working, I gradually realized that a program being able to complete a task does not necessarily mean that it is reliable.

A real file system contains many situations that the program has to handle safely.

## Path Validation

The `Organizer` class receives a folder path as its target:

```python
self.folder_path = Path(folder_path)
```

To prevent the program from working with an invalid path, I added two checks:

```python
if not self.folder_path.exists():
    raise ValueError("Path does not exist.")

if not self.folder_path.is_dir():
    raise ValueError("Path is not a folder.")
```

These two checks look similar, but they are actually testing two different conditions.

`exists()` asks:

> Does the object represented by this path actually exist?

`is_dir()` asks:

> Is this existing object a directory?

For example, if:

```text
test_folder/test.txt
```

does not exist, the program reports:

```text
Path does not exist.
```

Only when `test.txt` actually exists but is a file instead of a folder will the program report:

```text
Path is not a folder.
```

This helped me understand an important principle of exception handling:

> A program should report the problem that it can actually determine, rather than guessing what the user intended.

## Dealing with Real File Systems

While testing `scan_files()`, I found that the program also detected:

```text
desktop.ini
```

Even though this file was not visible in Windows Explorer, `Path.iterdir()` could still find it.

This showed me that the actual contents of a file system are not always exactly the same as what a graphical file manager displays to the user.

To avoid moving system-related files, I added an ignore list:

```python
IGNORED_FILES = {
    "desktop.ini",
}
```

Then I changed the scanning logic:

```python
if item.is_file() and item.name.lower() not in IGNORED_FILES:
    files.append(item)
```

Now File Organizer ignores `desktop.ini` instead of treating it like a normal user file.

This was one of the first moments in the project where I clearly realized that:

> Once a program starts interacting with a real operating system, it has to consider the environment it runs in, not just the Python code itself.

## Handling File Conflicts

Another real-world problem is filename conflicts.

For example:

```text
test_folder/
├── a.txt
└── Documents/
    └── a.txt
```

If the program simply moves the root-level `a.txt` into `Documents`, it may overwrite the existing file.

For the current v1.0 design, I chose a safer strategy:

```python
if destination.exists():
    return False
```

If the destination file already exists, the move is skipped.

If the move succeeds:

```python
return True
```

This means that `move_file()` no longer only performs an action. It also reports the result of that action back to the caller:

```python
if self.move_file(file, category):
    ...
else:
    ...
```

This helped me understand that:

> A return value can represent not only data, but also the result or status of an operation.

It also made the responsibilities of different methods clearer.

`move_file()` is responsible for:

```text
Moving the file
+
Reporting whether the move succeeded
```

while `organize()` is responsible for:

```text
Controlling the overall workflow
+
Responding to the result
```

## From `print()` to `logging`

At first, I used:

```python
print()
```

to display the result of each operation.

For example:

```text
Moved: b.jpg -> Images
Skipped: a.txt (already exists)
```

Later, I started using Python's:

```python
logging
```

module.

Successful moves now use:

```python
logging.info(...)
```

while skipped files use:

```python
logging.warning(...)
```

The output now looks more like:

```text
INFO: Moved: b.jpg -> Images
WARNING: Skipped: a.txt (already exists)
```

This helped me understand that logging and normal output are not exactly the same thing.

`print()` is mainly about:

> Displaying some text.

Logging is more about:

> Recording events that happen while the program is running.

Different log levels also represent different program states:

```text
INFO
→ Normal program activity

WARNING
→ Something unusual happened, but the program can continue

ERROR
→ An operation failed
```

## Logging Handlers

I then configured the program so that logs are written both to the terminal and to a log file.

I used:

```python
logging.StreamHandler()
```

to send logs to the terminal, and:

```python
logging.FileHandler()
```

to save them into:

```text
file_organizer.log
```

Now the same log message can be sent to multiple destinations.

This introduced me to the concept of a **logging handler**:

> A logger creates log records, while handlers determine where those records are sent.

The log file also includes timestamps, for example:

```text
2026-08-18 20:05:10 - INFO - Moved: b.jpg -> Images
```

This means that the program's execution history can be preserved even after the program has finished running.

## What I Learned

The main technical topics I learned during this stage include:

* `Path.exists()`
* `Path.is_dir()`
* Windows system and hidden files
* File ignore rules
* Filename conflict handling
* Using return values to represent operation results
* `logging`
* `INFO`
* `WARNING`
* `StreamHandler`
* `FileHandler`
* Log formatting and timestamps

However, the most important lesson was not any individual API.

I started to understand that:

> **“The program works” and “the program works reliably” are two different stages of software development.**

The first version of File Organizer could already:

```text
Scan → Categorize → Move
```

But only after I started considering invalid paths, system files, filename conflicts, and logging did it begin to feel more like a real software tool rather than just a programming exercise.

This project is also changing the way I think about development.

I am gradually moving from asking:

> “How do I make this feature work?”

to asking:

> “What could happen when this program runs in a real environment?”

The next stage will be to improve the command-line interface so that File Organizer can receive a target directory from the user instead of relying on a hard-coded test path.