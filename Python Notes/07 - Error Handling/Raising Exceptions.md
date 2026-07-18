# Raising Exceptions

## What is an Exception?

An exception is an error that occurs while a program is running.

When a function cannot continue because of invalid input or an unexpected situation, it should report the problem by raising an exception.


## Raising an Exception

Use the `raise` keyword to report an error.

Example:

```python
if age < 0:
    raise ValueError("Age cannot be negative.")
```

Another example:

```python
if username == "":
    raise ValueError("Username cannot be empty.")
```

Raising an exception immediately stops the current function.


## Raise vs Print

Do not confuse `raise` with `print`.

```python
print("Invalid input")
```

Only displays a message.

The program continues running.

```python
raise ValueError("Invalid input")
```

Reports an error and transfers control to the caller.


## Exception Propagation

Exceptions travel upward through the call stack until they are caught.

```text
main()
    │
    ▼
process_data()
    │
    ▼
validate_input()
    │
    ▼
raise ValueError(...)
```

If no function catches the exception, Python terminates the program and displays a traceback.


## Responsibilities

A function should detect problems.

The caller should decide how to respond.

Example:

```python
def validate_age(age: int):

    if age < 0:
        raise ValueError("Age cannot be negative.")
```

The caller handles the error:

```python
try:
    validate_age(age)
except ValueError as error:
    print(error)
```

This keeps error detection and error handling separate.


## When Should You Raise Exceptions?

Raise an exception when:

- Input is invalid.
- A required condition is not satisfied.
- The function cannot continue correctly.
- Returning a normal result would be misleading.


## Best Practices

- Raise specific exception types whenever possible.
- Write meaningful error messages.
- Let higher-level code decide how to handle errors.
- Do not use exceptions to replace normal program logic.


## Summary

- Use `raise` to report errors.
- Raising an exception stops the current function.
- Exceptions propagate until they are caught.
- Separate error detection from error handling.