# Object Validation and Constructor Design

## Introduction

When designing a class, creating a valid object is one of the constructor's most important responsibilities.

A well-designed object should always start in a valid state. Invalid data should be detected before the object is fully initialized.


## The Responsibility of `__init__()`

The constructor (`__init__`) is responsible for:

* Receiving input parameters
* Validating data
* Initializing object attributes
* Ensuring the object is created in a valid state

A constructor should never create an invalid object and then attempt to fix it afterward.


## Validate Before Assignment

Always validate data before assigning it to object attributes.

**Good Example**

```python
class User:

    def __init__(self, username):
        username = username.strip()

        if username == "":
            raise ValueError("Username cannot be empty.")

        self.username = username
```

**Avoid**

```python
class User:

    def __init__(self, username):
        self.username = username

        if self.username.strip() == "":
            raise ValueError("Username cannot be empty.")
```

Although the second example eventually raises an exception, the object temporarily enters an invalid state.


## Fail Fast Principle

**Fail Fast** means detecting problems as early as possible.

If invalid data is found, stop object creation immediately by raising an exception.

Benefits include:

* Preventing invalid objects from existing
* Making bugs easier to locate
* Simplifying debugging
* Improving code reliability


## Why Use `ValueError`

`ValueError` should be used when:

* The data type is correct.
* The value itself is invalid.

Example:

```python
User("")
```

The argument is a string, but an empty username is not acceptable.

```python
raise ValueError("Username cannot be empty.")
```


## Data Normalization

Before validation, it is often helpful to normalize input data.

A common example is removing accidental leading and trailing whitespace.

```python
username = username.strip()
```

Example:

Input:

```text
"   Alice   "
```

After normalization:

```text
"Alice"
```

Normalization keeps stored data clean and consistent.


## Required and Optional Parameters

When designing a constructor, consider three questions.

### 1. Is this parameter required?

If an object cannot exist without it, make it a required parameter.

Example:

```python
class User:

    def __init__(self, username):
        ...
```


### 2. If it is optional, what should the default value be?

Provide a default value only when it makes sense.

Example:

```python
class User:

    def __init__(self, username, bio=""):
        ...
```

An empty biography is a reasonable default because users may choose not to provide one.


### 3. Should the caller provide the value?

Sometimes an object should determine certain values itself.

For example:

```python
class User:

    def __init__(self, username):
        self.status = "active"
```

A newly created user always starts with the status `"active"`.


## Object Responsibility

A class should protect its own data.

If a class owns an attribute, it should also be responsible for validating that attribute.

This follows an important object-oriented design principle:

> A class should be responsible for maintaining its own valid state.


## Design Principle

> **Make invalid states impossible.**

A successfully created object should always satisfy its own rules.

Instead of fixing invalid data later, prevent invalid objects from being created in the first place.

This principle leads to code that is cleaner, safer, and easier to maintain.