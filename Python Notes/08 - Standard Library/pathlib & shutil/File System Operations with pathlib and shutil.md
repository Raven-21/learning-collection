# File System Operations with `pathlib` and `shutil`

## `Path`

`pathlib.Path` provides an object-oriented way to work with file system paths.

```python
from pathlib import Path
```

A path can be created from a string:

```python
path = Path("example/data.txt")
```

A `Path` object can represent either a file or a directory.

## Common Path Properties

### `name`

Returns the final component of the path.

```python
path = Path("example/data.txt")

print(path.name)
```

Output:

```text
data.txt
```

### `suffix`

Returns the file extension, including the leading dot.

```python
print(path.suffix)
```

Output:

```text
.txt
```

For case-insensitive comparisons, it is often useful to normalize the extension:

```python
suffix = path.suffix.lower()
```

### `stem`

Returns the filename without its extension.

```python
print(path.stem)
```

Output:

```text
data
```

### `parent`

Returns the parent directory.

```python
print(path.parent)
```

Output:

```text
example
```

## Checking Paths

### `exists()`

Checks whether a path exists.

```python
if path.exists():
    print("Path exists.")
```

### `is_file()`

Checks whether the path points to a file.

```python
if path.is_file():
    print("This is a file.")
```

### `is_dir()`

Checks whether the path points to a directory.

```python
if path.is_dir():
    print("This is a directory.")
```

These checks answer different questions.

```python
path.exists()
```

asks whether the path exists at all.

```python
path.is_dir()
```

asks whether an existing path represents a directory.

## Iterating Through a Directory

`iterdir()` returns the entries directly contained in a directory.

```python
folder = Path("example")

for item in folder.iterdir():
    print(item)
```

The entries may include both files and directories.

To process files only:

```python
for item in folder.iterdir():
    if item.is_file():
        print(item.name)
```

`iterdir()` does not guarantee alphabetical ordering.

If deterministic ordering is required:

```python
for item in sorted(folder.iterdir()):
    print(item)
```

## Building Paths

The `/` operator can be used to combine `Path` objects and path components.

```python
folder = Path("example")

file_path = folder / "data.txt"
```

This produces a path equivalent to:

```text
example/data.txt
```

This approach is preferable to manually joining path strings because `Path` handles platform-specific path behavior.

## Creating Directories

`mkdir()` creates a directory.

```python
folder = Path("example")

folder.mkdir()
```

If the directory may already exist:

```python
folder.mkdir(exist_ok=True)
```

This prevents an exception from being raised when the directory already exists.

To create missing parent directories as well:

```python
folder.mkdir(parents=True, exist_ok=True)
```

## Moving Files with `shutil`

The `shutil` module provides higher-level file operations.

```python
import shutil
```

A file can be moved with:

```python
source = Path("source/data.txt")
destination = Path("target/data.txt")

shutil.move(source, destination)
```

Before moving a file, it is often important to check whether the destination already exists:

```python
if not destination.exists():
    shutil.move(source, destination)
```

This can help prevent accidental overwriting.

## File Conflict Handling

A common file-system edge case occurs when the destination already contains a file with the same name.

Possible strategies include:

* Skip the file
* Overwrite the existing file
* Rename the incoming file
* Ask the user for a decision

A safe default is often to avoid overwriting automatically.

```python
if destination.exists():
    return False

shutil.move(source, destination)
return True
```

A Boolean return value can communicate whether the operation succeeded.

## Ignoring Specific Files

Some files may need to be excluded from processing.

An ignore set can be used:

```python
IGNORED_FILES = {
    "example.ini",
    "temporary.dat",
}
```

Then:

```python
if item.is_file() and item.name.lower() not in IGNORED_FILES:
    ...
```

Using `.lower()` allows case-insensitive filename comparisons.

## Key Idea

Working with a real file system requires more than simply reading and moving files.

A robust program should consider:

* Whether paths exist
* Whether a path is a file or directory
* Hidden or system-generated files
* Filename conflicts
* Missing directories
* Invalid paths
* Potential data loss

File-system code should generally prefer safe behavior over destructive behavior.