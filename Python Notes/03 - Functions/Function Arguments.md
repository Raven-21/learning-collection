# Function Arguments

## Overview

Function arguments allow values to be passed into a function when it is called.

Arguments make functions reusable and flexible by allowing the same function to work with different inputs.


## Positional Arguments

Positional arguments are matched according to their order.

```python
def greet(name, age):
    print(name, age)

greet("Tom", 20)
```

Output:

```text
Tom 20
```

The first value is assigned to `name`, and the second value is assigned to `age`.


## Default Arguments

A default argument provides a default value if no argument is given.

```python
def greet(name="Guest"):
    print(name)
```

```python
greet()
```

Output:

```text
Guest
```

Next:

```python
greet("Tom")
```

Output:

```text
Tom
```

Default arguments make parameters optional.


## Keyword Arguments

Arguments can also be passed by parameter name.

```python
def greet(name, age):
    print(name, age)

greet(age=20, name="Tom")
```

Output:

```text
Tom 20
```

When using keyword arguments, the order no longer matters.


## Mixing Positional and Keyword Arguments

Positional arguments can be combined with keyword arguments.

```python
def greet(name, age, country="Unknown"):
    print(name, age, country)

greet("Tom", age=20)
```

Output:

```text
Tom 20 Unknown
```

Rules:

* Positional arguments must come before keyword arguments.
* Keyword arguments can appear in any order.


## Parameter Order

When defining a function, required parameters must come before default parameters.

Correct:

```python
def create_game(max_chance, number=None, history=None):
    ...
```

Incorrect:

```python
def create_game(number=None, max_chance):
    ...
```

This produces a syntax error because Python requires all required parameters to appear before parameters with default values.


## Practical Example

In the Guess the Number project:

```python
class Game:

    def __init__(
        self,
        max_chance,
        number=None,
        history=None
    ):
        ...
```

This constructor supports two situations.

Create a new game:

```python
game = Game(10)
```

Restore a saved game:

```python
game = Game(
    max_chance=10,
    number=34,
    history=[
        {
            "guess": 50,
            "result": "high"
        }
    ]
)
```

Using keyword arguments makes the code easier to read and understand.


## Best Practices

* Put required parameters before optional parameters.
* Use default arguments only when appropriate.
* Prefer keyword arguments when a function has many parameters.
* Use keyword arguments to improve readability.
* Use `None` instead of mutable objects (such as `[]` or `{}`) as default values.


## Summary

* Positional arguments are matched by order.
* Default arguments provide optional values.
* Keyword arguments are matched by parameter name.
* Required parameters must come before default parameters.
* Keyword arguments improve readability, especially in functions with multiple parameters.
* `None` is commonly used as the default value for mutable objects.