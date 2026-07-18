# Type Hints

## What are Type Hints?

Type hints describe the expected types of function parameters and return values.

Example:

```python
def add(a: int, b: int) -> int:
    return a + b
```

Here:

- `a` is expected to be an integer.
- `b` is expected to be an integer.
- The function returns an integer.


## Parameter Type Annotations

Function parameters can specify their expected types.

```python
def greet(name: str):
    print(f"Hello, {name}")
```

```python
def repeat(text: str, times: int):
    ...
```

Type annotations make function signatures easier to understand.


## Return Type Annotations

The symbol `->` specifies the return type.

Examples:

```python
def is_even(number: int) -> bool:
    return number % 2 == 0
```

```python
def read_lines() -> list[str]:
    ...
```

```python
def calculate_total() -> float:
    ...
```

```python
def save_data() -> None:
    ...
```


## Why Use Type Hints?

Type hints are optional.

They do **not** affect how Python executes code.

Their main benefits are:

- Better readability
- Better IDE support
- Better auto-completion
- Easier maintenance
- Better static analysis


## Type Hints Improve Communication

Type hints make code easier to understand for both humans and development tools.

They describe how a function is intended to be used without changing its behavior.


## Summary

Type hints document the expected types of code.

They improve readability and maintainability while remaining completely optional.