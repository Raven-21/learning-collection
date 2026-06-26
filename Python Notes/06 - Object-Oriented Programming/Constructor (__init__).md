# OOP - Constructor (**init**)

## What is **init**()?

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


## Purpose of **init**()

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