# Type Hints

## What are Type Hints?

Type hints describe the expected types of function parameters and return values.

Example:

```python
def update_task(index: int, title: str, description: str) -> None:
    ...
```

Here:

- `index` is expected to be an integer.
- `title` is expected to be a string.
- `description` is expected to be a string.
- `None` means the function does not return a value.


## Parameter Type Annotations

Function parameters can specify their expected types.

```python
def greet(name: str):
    ...
```

```python
def add(a: int, b: int):
    ...
```

This makes function signatures easier to understand.


## Return Type Annotations

The symbol `->` specifies the return type.

Examples:

```python
def add(a: int, b: int) -> int:
    return a + b
```

```python
def is_valid() -> bool:
    return True
```

```python
def get_tasks() -> list[Task]:
    return self.tasks.copy()
```

```python
def update() -> None:
    ...
```


## Why Use Type Hints?

Type hints are optional.

They do **not** change how Python executes code.

Their main benefits are:

- Better readability
- Better IDE support
- Better auto-completion
- Easier maintenance
- Better static analysis


## Summary

Type hints help describe the intended use of code.

They improve code quality without affecting program behavior.