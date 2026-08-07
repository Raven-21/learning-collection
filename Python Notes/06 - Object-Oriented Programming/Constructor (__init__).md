# OOP - Constructor (`__init__()`)


## What is `__init__()`?

`__init__()` is a special method that is automatically called when an object is created.

```python
class TestObj:

    def __init__(self, number):
        self.number = number
```

```python
obj_1 = TestObj(3)
```

Python automatically calls:

```python
obj_1.__init__(3)
```


## Purpose of `__init__()`

The purpose of `__init__()` is to initialize the object's state.

Example:

```python
class TestObj:

    def __init__(self, number):
        self.number = number
        self.my_list = []
```

After creation:

```python
obj_1 = TestObj(3)
```

The object contains:

```python
obj_1.number
obj_1.my_list
```


## Alternative Constructors with `@classmethod`

A class can provide additional ways to create objects through class methods.

A class method is defined using the `@classmethod` decorator. Its first parameter is conventionally named `cls`, which refers to the class itself.

Example:

```python
class User:

    def __init__(self, name: str, email: str) -> None:
        self.name = name
        self.email = email

    @classmethod
    def from_dict(cls, data: dict) -> "User":
        return cls(
            data["name"],
            data["email"],
        )
```

The normal constructor creates an object from individual arguments:

```python
user = User(
    "Alice",
    "alice@example.com"
)
```

The class method provides an alternative construction interface:

```python
data = {
    "name": "Alice",
    "email": "alice@example.com"
}

user = User.from_dict(data)
```

Inside the class method:

```python
cls(...)
```

creates an instance of the current class.

Using `cls` instead of writing the class name directly also allows the method to work correctly with subclasses.

Class methods are commonly used as **alternative constructors** when objects need to be created from another representation, such as:

* Dictionaries
* Strings
* Configuration data
* Database records


## Important Notes

`__init__()` initializes an object.

It does not create the object itself.

Conceptually:

```text
Create Object
        ↓
Call __init__()
        ↓
Initialize State
```


## Summary

* `__init__()` is a special method.
* It runs automatically when an object is created.
* It is used to initialize object state.
* Object state is usually stored through `self`.
* `@classmethod` can provide alternative ways to construct objects.
* `cls` refers to the current class inside a class method.