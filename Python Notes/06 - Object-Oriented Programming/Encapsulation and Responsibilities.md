# Encapsulation and Responsibilities

## What is Encapsulation?

Encapsulation is one of the fundamental principles of Object-Oriented Programming (OOP).

It means that an object should manage its own data and behavior instead of exposing its internal implementation.

For example, instead of modifying an object's attributes directly:

```python
account.balance = -100
```

provide a public method:

```python
account.withdraw(100)
```

The object becomes responsible for validating and updating its own state.


## Public Methods and Internal Methods

A class usually provides **public methods** for other code to use.

Sometimes, a public method needs help from another method that is only part of the class implementation.

Example:

```python
class User:

    def change_email(self, email: str):
        self.email = self._validate_email(email)

    def _validate_email(self, email: str) -> str:
        email = email.strip()

        if "@" not in email:
            raise ValueError("Invalid email address.")

        return email
```

Here:

- `change_email()` is a public method.
- `_validate_email()` is an internal helper method.


## Internal Helper Methods

Methods beginning with a single underscore (`_`) are intended for internal use.

Python does **not** prevent external code from calling them.

The underscore is simply a convention that tells other developers:

> This method is part of the internal implementation.

Internal helper methods should normally only be used inside the class.


## Avoid Code Duplication

Suppose both object creation and object updates need to validate an email address.

Instead of writing the same validation code twice:

```text
__init__()
    ↓
validate email

change_email()
    ↓
validate email
```

Extract the shared logic into a helper method:

```text
__init__()
        │
        ▼
_validate_email()

change_email()
        │
        ▼
_validate_email()
```

This makes the program easier to maintain.


## Responsibility of Each Class

A class should manage its own data and behavior.

Another class should communicate through public methods instead of modifying internal data directly.

This keeps responsibilities clear and reduces coupling between classes.


## Related Design Principle

Extracting shared logic into helper methods follows the **DRY (Don't Repeat Yourself)** principle.

Reducing duplicated code improves consistency and maintainability.


## Summary

Good encapsulation means:

- Objects manage themselves.
- Internal implementation is hidden behind public methods.
- Helper methods reduce duplicated code.
- Each class has clear responsibilities.