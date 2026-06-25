# Python Data Types

## 1. What are Data Types?

In Python, every value has a **type**.

A data type tells Python:
- what kind of data it is
- what operations can be done with it


## 2. Main Built-in Data Types

Python has several basic data types:

- `str` → String
- `int` → Integer
- `float` → Floating point number
- `bool` → Boolean


## 3. String (str)

Used for text.

```python
name = "Tom"
message = "Hello World"
```

### Notes:
- Must use quotes `" "` or `' '`
- Can contain letters, numbers, symbols


## 4. Integer (int)

Used for whole numbers.

```python
age = 23
score = 100
```

### Notes:
- No decimal point
- Can be positive or negative


## 5. Float

Used for decimal numbers.

```python
height = 1.75
price = 9.99
```

### Notes:
- Contains decimal point
- Used for measurements, money, etc.


## 6. Boolean (bool)

Used for True / False values.

```python
is_student = True
is_passed = False
```

### Notes:
- Only two values: `True` or `False`
- Used in conditions and logic


## 7. Checking Data Type

Use `type()` to check a variable type:

```python
x = 10
print(type(x))
```

Output:
```
<class 'int'>
```


## 8. Type Conversion

You can convert between types.

### String → Integer

```python
age = "23"
age = int(age)
```


### Integer → String

```python
age = 23
age = str(age)
```


### Integer → Float

```python
x = 10
x = float(x)
```


## 9. Common Mistake

```python
age = "23"
print(age + 1)
```

❌ Error:
- string + int cannot be combined


## 10. Correct Version

```python
age = int("23")
print(age + 1)
```


## 11. Dynamic Typing (Very Important)

Python is dynamically typed:

```python
x = 10
x = "hello"
```

👉 The type can change anytime.


## 12. Type Summary Table

| Type  | Example       | Description        |
|------|--------------|--------------------|
| str  | "hello"      | Text               |
| int  | 10           | Whole number       |
| float| 3.14         | Decimal number     |
| bool | True/False   | Logic value        |


## 13. Real Example

```python
name = "Tom"
age = 23
height = 1.75
is_student = True

print(f"{name} is {age} years old.")
```


## 14. Key Takeaways

- Every value in Python has a type
- Main types: `str`, `int`, `float`, `bool`
- Use `type()` to check type
- Use conversion functions when needed
- Python is dynamically typed


## 15. Think Like a Programmer

```text
Data → Type → Operation → Result
```

Understanding data types is the foundation of all programming logic.