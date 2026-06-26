# Python Error Handling - try / except

## What is Error Handling?

Error handling is a way to prevent programs from crashing when unexpected problems happen.

In simple words:

> “Try to run code, and handle errors safely if something goes wrong.”


## Why is Error Handling Important?

Programs often receive unexpected input.

Example:

```python
age = int(input("Enter age: "))
```

If the user enters:

```text
abc
```

Python crashes with an error.

Without error handling:
- program stops
- user experience becomes poor


## Basic try / except Structure

```python
try:
    # code that may cause error
except:
    # code that runs if error happens
```


## Simple Example

```python
try:
    number = int(input("Enter number: "))
    print(number)
except:
    print("Invalid input")
```


## How It Works

### Step 1

Python tries to run:

```python
number = int(input())
```


### Step 2

If no error happens:
- program continues normally

If an error happens:
- Python jumps to `except`


## Real Example

```python
try:
    age = int(input("Enter age: "))
    print(f"You are {age} years old")
except:
    print("Please enter a valid number")
```


## Handling Specific Errors

You can catch specific error types.

Example:

```python
try:
    number = int(input())
except ValueError:
    print("Invalid number")
```


## Common Error Types

| Error Type | Meaning |
|---|---|
| `ValueError` | wrong value type |
| `TypeError` | wrong operation between types |
| `NameError` | variable not defined |
| `ZeroDivisionError` | division by zero |
| `IndexError` | invalid list index |


## Example: Division Error

```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
```


## Using else

`else` runs if no error occurs.

```python
try:
    number = int(input("Enter number: "))
except ValueError:
    print("Invalid input")
else:
    print("Success")
```


## Using finally

`finally` always runs.

```python
try:
    print("Start")
except:
    print("Error")
finally:
    print("Finished")
```


## Common Beginner Mistakes

### 1️⃣ Using try everywhere

❌ Bad:

```python
try:
    # huge program
except:
    print("Error")
```

Use error handling only where needed.


### 2️⃣ Hiding all errors

```python
except:
    pass
```

This can hide important problems.


### 3️⃣ Forgetting proper validation

Error handling is helpful, but programs should still validate input carefully.


## Error Handling Flow

```text
Run code
   ↓
Error?
 ├── No → continue normally
 └── Yes → run except block
```


## Real Example: Input Validation Loop

```python
while True:
    try:
        number = int(input("Enter number: "))
        break
    except ValueError:
        print("Please enter a valid integer")
```

This is a very common real-world pattern.


## Why try / except Matters

Error handling improves:

- program stability
- user experience
- robustness
- reliability

Without it, programs crash easily.


## Think Like a Software Engineer

```text
Users do unexpected things.
Programs should handle them safely.
```

Good software expects mistakes and handles them gracefully.


## Real Usage in Projects

Error handling is used everywhere:

- user input systems
- APIs
- file operations
- web applications
- AI tools
- automation scripts


## Key Ideas

- `try` → attempt risky code
- `except` → handle errors safely
- prevents crashes
- improves robustness
- essential for real software


## Final Summary

```text
Good programs do not assume everything will work perfectly.

They prepare for errors and handle them properly.
```