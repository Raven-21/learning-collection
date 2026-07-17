# Encapsulation and Responsibilities

## What is Encapsulation?

Encapsulation is one of the fundamental ideas of Object-Oriented Programming (OOP).

A class should manage its own data and behavior instead of allowing external code to modify its internal state directly.

Instead of doing this:

```python
task.title = title
task.description = description
```

Expose a public method:

```python
task.update(title, description)
```

The object becomes responsible for updating itself.


## Internal Helper Methods

Sometimes multiple methods need the same logic.

Instead of duplicating code, extract it into an internal helper method.

Example:

```python
def _validate_title(self, title: str) -> str:
    title = title.strip()

    if title == "":
        raise ValueError("Title cannot be empty.")

    return title
```

Methods beginning with a single underscore (`_`) are intended for internal use.

Python does **not** prevent external code from calling them.

The underscore simply tells other developers:

> This method is part of the class implementation and should normally not be called directly.


## Avoid Code Duplication

Without a helper method:

```python
__init__()
```

and

```python
update()
```

would both contain the same validation code.

Instead:

```text
__init__()
        │
        ▼
_validate_title()

update()
        │
        ▼
_validate_title()
```

Both methods reuse the same validation logic.

This follows the **DRY (Don't Repeat Yourself)** principle.


## Responsibility of Each Class

Each class should only manage its own responsibilities.

### TaskManager

- Store tasks
- Find tasks
- Validate task indexes
- Delegate work to Task objects

### Task

- Store task data
- Validate titles
- Update its own state

Keeping responsibilities separate makes the program easier to maintain and extend.


## Summary

Good OOP design means:

- Objects manage themselves.
- Helper methods reduce duplicated code.
- Validation belongs to the class that owns the data.
- Each class has clear responsibilities.