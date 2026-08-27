# Command-Line Argument Parsing with `argparse`

## What Is `argparse`?

`argparse` is a module in the Python standard library for building command-line interfaces.

It allows a program to receive values and options when it is started from a terminal.

```python
import argparse
```

For example:

```bash
python main.py data
```

The value:

```text
data
```

can be parsed and used inside the Python program.

## Creating an Argument Parser

A parser is created with:

```python
parser = argparse.ArgumentParser()
```

A description can also be provided:

```python
parser = argparse.ArgumentParser(
    description="Process files from a target directory."
)
```

The description is displayed when the user requests help.

## Defining Arguments

Arguments are registered with:

```python
parser.add_argument(...)
```

For example:

```python
parser.add_argument(
    "path",
    help="Path to the target directory."
)
```

This defines a positional command-line argument named `path`.

## Positional Arguments

A positional argument is identified by its position in the command.

For example:

```python
parser.add_argument("path")
```

can be used as:

```bash
python main.py data
```

After parsing:

```python
args.path
```

contains:

```text
data
```

Because positional arguments are normally required, running the program without the value results in an error.

```bash
python main.py
```

Possible output:

```text
error: the following arguments are required: path
```

## Optional Arguments

Optional arguments usually begin with one or two hyphens.

For example:

```python
parser.add_argument(
    "--verbose",
    help="Enable additional output."
)
```

They are explicitly named when the command is executed:

```bash
python main.py data --verbose
```

A common convention is:

```text
-h
-v
```

for short options, and:

```text
--help
--verbose
```

for long options.

## Boolean Flags

Options that simply enable or disable a behavior can use:

```python
action="store_true"
```

Example:

```python
parser.add_argument(
    "--verbose",
    action="store_true",
    help="Enable verbose output."
)
```

Without the flag:

```bash
python main.py data
```

the value is:

```python
args.verbose == False
```

With the flag:

```bash
python main.py data --verbose
```

the value becomes:

```python
args.verbose == True
```

This is useful for command-line switches.

## Hyphens and Python Attribute Names

Command-line options commonly use hyphens:

```text
--dry-run
```

Python identifiers cannot contain hyphens, so `argparse` automatically converts them to underscores.

For example:

```python
parser.add_argument("--dry-run")
```

is accessed as:

```python
args.dry_run
```

The relationship is:

```text
--dry-run
    ↓
args.dry_run
```

## Parsing Arguments

After arguments have been defined, the actual command-line input is parsed using:

```python
args = parser.parse_args()
```

The parser reads the values supplied when the program was launched and stores them in `args`.

For example:

```bash
python main.py data --verbose
```

may produce:

```python
args.path
# "data"

args.verbose
# True
```

The basic pattern is:

```text
ArgumentParser()
→ create the parser

add_argument()
→ define accepted arguments

parse_args()
→ read command-line input

args.<name>
→ access parsed values
```

## Automatic Help

`argparse` automatically provides:

```bash
python main.py --help
```

or:

```bash
python main.py -h
```

This can display:

* Program usage
* Program description
* Positional arguments
* Optional arguments
* Help text for each argument

This makes basic command-line documentation available without manually implementing it.

## Command-Line Arguments vs `input()`

Command-line arguments and `input()` both receive data from users, but at different times.

With `input()`:

```text
Program starts
→ program asks for input
→ user responds
→ program continues
```

With command-line arguments:

```text
User writes command and arguments
→ program starts
→ arguments are parsed
→ program runs
```

Example with `input()`:

```python
name = input("Enter your name: ")
```

Example with command-line arguments:

```bash
python main.py Alice
```

Command-line arguments are especially useful for:

* Utility programs
* Automation
* Scripts
* Development tools
* Programs called by other programs

## Passing Parsed Arguments to Functions

Parsed arguments are ordinary Python values.

They can be passed into functions or constructors:

```python
run(
    path=args.path,
    verbose=args.verbose
)
```

Here:

```python
args.path
```

comes from the command line, while:

```python
path=
```

is a Python keyword argument used in the function call.

These concepts belong to different layers:

```text
Command line:
positional arguments
optional arguments

Python function calls:
positional arguments
keyword arguments
```

They should not be confused with each other.

## Dry-Run Style Flags

A common command-line pattern is a dry-run flag:

```python
parser.add_argument(
    "--dry-run",
    action="store_true",
    help="Preview operations without making changes."
)
```

Then:

```python
if args.dry_run:
    ...
```

can be used to avoid performing destructive actions.

Dry-run behavior is useful when programs modify:

* Files
* Directories
* Databases
* Configuration
* Remote systems

The key principle is:

> A dry run should report intended operations without producing real side effects.

## Basic Structure

A typical command-line program may look like:

```python
import argparse


def main() -> None:
    parser = argparse.ArgumentParser(
        description="Example command-line program."
    )

    parser.add_argument("path")

    parser.add_argument(
        "--verbose",
        action="store_true"
    )

    args = parser.parse_args()

    print(args.path)
    print(args.verbose)


if __name__ == "__main__":
    main()
```

## Key Idea

`argparse` separates command-line input from program logic.

A program can define what information it accepts, validate basic command syntax automatically, and expose a more structured interface than relying only on interactive `input()` calls.