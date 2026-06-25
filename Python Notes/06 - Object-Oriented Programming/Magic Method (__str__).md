# OOP - Magic Method (**str**)

## What is **str**()?

`__str__()` is a special method used to define how an object is displayed as a string.

Example:

```python
class TestObj:

    def __str__(self):
        return "Test Object"
```

obj_1 = TestObj()

## Automatic Calls

```python
print(obj_1)
```

Equivalent to:

```python
print(str(obj_1))
```

Which eventually calls:

```python
obj_1.__str__()
```

## Example

```python
class TestObj:

    def __init__(self, number):
        self.number = number

    def __str__(self):
        return f"TestObj(Number: {self.number})"
```

Output:

```python
obj_1 = obj_1(10)

print(obj_1)
```

```text
TestObj(Number: 3)
```


## Summary

* `__str__()` controls how an object is printed.
* It returns a string.
* `print(object)` automatically uses `__str__()`.
* It is a Magic Method (Special Method).