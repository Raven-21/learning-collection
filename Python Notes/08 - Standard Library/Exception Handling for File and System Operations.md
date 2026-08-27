# Exception Handling for File and System Operations

## Why File Operations Can Fail

Operations involving files and directories depend on the operating system.

Even when program logic is correct, an operation may fail because of external conditions such as:

* Missing paths
* Permission restrictions
* Locked or unavailable files
* Invalid file-system states
* Device errors
* Operating-system limitations

For this reason, file-system code often requires deliberate exception handling.

## Validating Paths

Before performing an operation, it is useful to validate the target path.

```python
from pathlib import Path


path = Path("example")
```

### Checking Whether a Path Exists

```python
if not path.exists():
    raise ValueError("Path does not exist.")
```

`exists()` answers:

> Does an object exist at this path?

### Checking Whether a Path Is a Directory

```python
if not path.is_dir():
    raise ValueError("Path is not a directory.")
```

`is_dir()` answers:

> Does this existing path represent a directory?

These checks should normally occur in this order:

```text
Does the path exist?
        ↓
Is it the expected type?
```

A nonexistent path cannot meaningfully be treated as an existing file or directory.

## Raising Exceptions

A function or class can use `raise` when it detects an invalid state.

```python
if not path.exists():
    raise ValueError("Path does not exist.")
```

Raising an exception separates:

```text
detecting a problem
```

from:

```text
deciding how the problem should be presented
```

This allows higher-level code to choose how to respond.

## Catching Exceptions

Exceptions can be handled using:

```python
try:
    ...
except SomeError:
    ...
```

Example:

```python
try:
    process_path(path)

except ValueError as error:
    print(error)
```

The code inside `try` is executed normally.

If the specified exception occurs, control moves to the matching `except` block.

## `ValueError`

`ValueError` is useful when a value is structurally valid Python data but unsuitable for the operation.

For example:

```python
if not path.exists():
    raise ValueError("Path does not exist.")
```

or:

```python
if not path.is_dir():
    raise ValueError("Path is not a directory.")
```

The problem is not necessarily the Python type itself. The problem is that the supplied value is invalid for the current operation.

## `PermissionError`

`PermissionError` occurs when the operating system refuses an operation because of insufficient permissions.

Example:

```python
try:
    perform_file_operation()

except PermissionError:
    print("Permission denied.")
```

Possible causes include:

* Insufficient user privileges
* Protected directories
* Restricted system files
* Operating-system security rules

## `OSError`

`OSError` represents a broader category of operating-system-related failures.

Example:

```python
try:
    perform_file_operation()

except OSError as error:
    print(f"Operation failed: {error}")
```

It can represent problems involving:

* Files
* Directories
* Devices
* Paths
* Other operating-system resources

Many more specific exceptions are subclasses of `OSError`.

## Specific Exceptions Before General Exceptions

When multiple related exceptions are handled, the more specific exception should normally appear first.

```python
try:
    perform_file_operation()

except PermissionError:
    print("Permission denied.")

except OSError as error:
    print(f"Operating-system error: {error}")
```

This works because `PermissionError` is more specific.

The specific handler allows the program to provide a more meaningful response.

The broader `OSError` handler can then catch other system-related failures.

## Separating Error Detection and Presentation

A useful design pattern is:

```text
Lower-level component
→ detects invalid state
→ raises exception

Higher-level application
→ catches exception
→ decides how to display or log it
```

For example:

```python
def validate_directory(path: Path) -> None:
    if not path.exists():
        raise ValueError("Path does not exist.")
```

Then:

```python
try:
    validate_directory(path)

except ValueError as error:
    logging.error(error)
```

This keeps validation logic separate from user-interface behavior.

## Exceptions vs Return Values

Not every unsuccessful operation requires an exception.

A function may return a status value for an expected condition:

```python
if destination.exists():
    return "skipped"
```

while unexpected system failures may be handled as exceptions:

```python
try:
    move_file()

except OSError:
    return "failed"
```

A useful distinction is:

```text
Expected alternative outcome
→ return value or status

Unexpected failure
→ exception
```

The exact design depends on the program.

## Avoiding Ambiguous Boolean Results

A Boolean result can be useful when only two outcomes exist:

```python
True
False
```

However, it becomes unclear when several outcomes are possible.

For example:

```text
Moved successfully
Skipped because destination exists
Failed because of permissions
Failed because of another system error
```

Representing all unsuccessful outcomes as:

```python
False
```

loses information.

A more expressive result may use explicit states:

```python
"moved"
"skipped"
"failed"
```

This makes downstream logic easier to understand.

## Logging Errors

Errors in command-line or background tools are often better recorded with `logging` than with raw `print()` calls.

```python
import logging


try:
    perform_operation()

except PermissionError:
    logging.error("Permission denied.")
```

This allows errors to share the same logging system used for:

* Normal events
* Warnings
* Failures
* Persistent log files

## User-Facing Errors and Tracebacks

During development, a traceback is useful because it contains technical debugging information.

A normal user may instead need a concise message:

```text
ERROR: Path does not exist.
```

A program can catch expected exceptions at an outer layer and present a cleaner message.

Unexpected programming errors should not necessarily be hidden automatically, because their tracebacks may be important for debugging.

## Error Handling Should Not Hide Problems

Exception handling should not be used merely to prevent a program from crashing.

This is usually a poor pattern:

```python
try:
    perform_operation()

except Exception:
    pass
```

It hides the cause of failures and makes debugging difficult.

A better approach is to:

* Catch exceptions intentionally
* Handle only errors that can be meaningfully handled
* Record useful information
* Allow unexpected problems to remain visible when appropriate

## Key Idea

Robust exception handling is about defining responsibility.

Lower-level code should detect failures accurately.

Higher-level code should decide whether to:

* Retry
* Skip
* Report
* Log
* Stop execution

The goal is not simply to prevent errors from appearing, but to make failures understandable and predictable.