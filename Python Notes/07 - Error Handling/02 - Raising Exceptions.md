# Raising Exceptions

## What is an Exception?

An exception is an error that occurs while a program is running.

Sometimes a function cannot continue because the input or program state is invalid.

In these situations, the function should report the problem by raising an exception.


## Raising an Exception

Use the `raise` keyword to report an error.

Example:

```python
raise ValueError("Title cannot be empty.")
```

Another example:

```python
if not (0 <= index < len(self.tasks)):
    raise ValueError("Invalid task number.")
```

Raising an exception immediately stops the current function and passes the error to the caller.


## Why Raise Exceptions?

Instead of silently ignoring problems, a function should clearly report when something is wrong.

For example:

```python
def divide(a, b):
    if b == 0:
        raise ValueError("The divisor cannot be zero.")

    return a / b
```

The function does not try to recover from the error.

It simply reports the problem.


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

Reports an error and immediately stops the current function.

The caller must decide how to handle the exception.


## Exception Propagation

Exceptions travel upward through the call stack until they are caught.

Example:

```text
main()
    │
    ▼
update_task()
    │
    ▼
Task.update()
    │
    ▼
_validate_title()
    │
    ▼
raise ValueError(...)
```

If no function catches the exception, Python terminates the program and displays a traceback.


## Responsibilities

A function should only be responsible for detecting problems.

It should not decide how the program responds.

Example:

```python
def update(self, title):
    if title.strip() == "":
        raise ValueError("Title cannot be empty.")
```

The caller decides what to do:

```python
try:
    task.update(title)
except ValueError as error:
    print(error)
```

This keeps responsibilities separated.


## When Should You Raise Exceptions?

Raise an exception when:

- Input is invalid.
- A required condition is not satisfied.
- The function cannot continue correctly.
- Returning a normal result would be misleading.

Do not raise exceptions for situations that are part of normal program flow.


## Best Practices

- Raise specific exception types whenever possible.
- Provide clear and meaningful error messages.
- Let higher-level code decide how to handle errors.
- Do not use `raise` to replace normal program logic.


## Summary

- Use `raise` to report errors.
- Raising an exception stops the current function.
- Exceptions propagate until they are caught.
- Functions should report problems, not decide how to recover.
- Separate error detection from error handling.