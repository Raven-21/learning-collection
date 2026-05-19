# Python Variables

## 1. What is a Variable?

A variable is a container used to store data in Python.

You can think of it as a **label pointing to a value in memory**.


## 2. Basic Syntax

```python
name = "Tom"
age = 23
```

### Explanation:
- `name` → variable name
- `"Tom"` → string value
- `age` → integer value
- `23` → number value


## 3. Variable Naming Rules

### ✅ Valid names:
```python
name = "Alice"
user_age = 20
age1 = 30
```

### ❌ Invalid names:
```python
1name = "Tom"     # cannot start with number
user-name = "Tom" # cannot use hyphen
```


## 4. Common Data Types

Variables can store different types of data:

### String (str)
```python
name = "Tom"
```

### Integer (int)
```python
age = 23
```

### Float
```python
height = 1.75
```

### Boolean (bool)
```python
is_student = True
```


## 5. Dynamic Typing

Python does NOT require you to declare variable types.

```python
x = 10
x = "hello"
```

👉 The type can change during runtime.


## 6. Multiple Assignment

You can assign multiple variables at once:

```python
a, b, c = 1, 2, 3
```


## 7. Reassigning Variables

Variables can be updated:

```python
score = 10
score = 20
```


## 8. Printing Variables

```python
name = "Tom"
print(name)
```

Output:
```
Tom
```


## 9. String + Variable Output

### Method 1: Comma in print
```python
name = "Tom"
print("Hello", name)
```

### Method 2: f-string (Recommended)
```python
name = "Tom"
print(f"Hello {name}")
```


## 10. Type Checking

```python
x = 10
print(type(x))
```

Output:
```
<class 'int'>
```


## 11. Type Conversion

```python
age = 23
age_str = str(age)
```

Common conversions:
- `str()`
- `int()`
- `float()`


## 12. Key Ideas to Remember

- Variables store data
- Python is dynamically typed
- Variable names must follow rules
- f-strings are the modern way to format output
- Types can be converted when needed


## 13. Real Usage Example

```python
name = "Tom"
age = 23

print(f"My name is {name} and I am {age} years old.")
```
