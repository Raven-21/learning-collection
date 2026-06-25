# File I/O

## What is File I/O?

File I/O (Input / Output) is used to read data from files and write data to files.

It allows data to persist after a program exits.

Without file storage:

```text
Program Starts
    ↓
Data Created
    ↓
Program Ends
    ↓
Data Lost
```

With file storage:

```text
Program Starts
    ↓
Data Created
    ↓
Save to File
    ↓
Program Ends
    ↓
Data Remains
```


## Opening a File

Use `open()` to open a file.

```python
file = open("data.txt")
```

However, the recommended way is:

```python
with open("data.txt") as file:
    ...
```


## The `with` Statement

The `with` statement automatically closes the file after use.

```python
with open("data.txt", "r") as file:
    content = file.read()
```

Equivalent to:

```python
file = open("data.txt", "r")

content = file.read()

file.close()
```

Using `with` is safer and cleaner.


## Common File Modes

| Mode  | Description                             |
| ----- | --------------------------------------- |
| `"r"` | Read file                               |
| `"w"` | Write file (overwrite existing content) |
| `"a"` | Append to file                          |
| `"x"` | Create a new file                       |


## Reading a File

### Read Entire File

```python
with open("data.txt", "r") as file:
    content = file.read()
```


### Read Line by Line

```python
with open("data.txt", "r") as file:
    for line in file:
        print(line)
```


## Writing to a File

### Overwrite Mode

```python
with open("data.txt", "w") as file:
    file.write("Hello World")
```

If the file already contains data, the old content will be removed.


### Append Mode

```python
with open("data.txt", "a") as file:
    file.write("New Line\n")
```

Append mode keeps existing content and adds new content to the end of the file.


## Writing Multiple Lines

```python
with open("data.txt", "a") as file:
    file.write("Line 1\n")
    file.write("Line 2\n")
    file.write("Line 3\n")
```


## Newline Character

```python
"\n"
```

Represents a newline.

Example:

```python
file.write("Hello\n")
file.write("World\n")
```

Produces:

```text
Hello
World
```


## File Encoding

Recommended:

```python
with open(
    "data.txt",
    "r",
    encoding="utf-8"
) as file:
```

UTF-8 supports most modern languages and symbols.

Using UTF-8 helps avoid encoding issues.


## File Object

The variable after `as` is called a file object.

```python
with open("data.txt") as file:
```

Here:

```python
file
```

is the file object.

It provides methods such as:

```python
file.read()

file.write()

file.close()
```


## Persistence

Persistence means data can survive after the program exits.

Examples:

* Save game records
* Save configuration files
* Save user settings
* Save logs
* Save application data

Persistence is one of the most common uses of File I/O.


## Practical Example

```python
with open(
    "game_history.txt",
    "a",
    encoding="utf-8"
) as file:

    file.write("=== GAME SUMMARY ===\n")
    file.write("Answer: 42\n")
    file.write("Attempts: 5\n")
```

Result:

```text
=== GAME SUMMARY ===
Answer: 42
Attempts: 5
```


## Key Concepts

* File I/O
* File Object
* Read
* Write
* Append
* Encoding
* Persistence
* Context Manager (`with`)