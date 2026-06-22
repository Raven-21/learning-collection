# OOP - self

## What is self?

`self` refers to the current object.

Example:

```python
class TestObj:

    def __init__(self, number):
        self.number = number
        self.list = []
```

When:

```python
Obj_1 = TestObj(3)
```

`self` refers to:

```python
Obj_1
```


## Object Attributes

```python
self.number = number
```

Left side:

```python
self.number
```

Object attribute.

Right side:

```python
number
```

Function parameter.


## Why use self?

Without `self`:

```python
def __init__(self):
    list = []
```

`list` is only a local variable.

It disappears after the function ends.

With `self`:

```python
self.list = []
```

The data becomes part of the object.


## Summary

* `self` represents the current object.
* `self.attribute` stores data inside the object.
* Without `self`, variables are only local variables.
* Every object has its own independent attributes.