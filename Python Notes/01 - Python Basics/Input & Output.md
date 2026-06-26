# Python Input / Output

## What is Input and Output?

In Python:

- **Input** = data entered by the user
- **Output** = data displayed by the program


## Output (print)

### Basic usage

```python
print("Hello World")
```

Output:
```
Hello World
```


### Printing variables

```python
name = "Tom"
print(name)
```

Output:
```
Tom
```


## Multiple Outputs

### Using comma (automatic space)

```python
name = "Tom"
print("Hello", name)
```

Output:
```
Hello Tom
```

👉 Python automatically adds a space between values.


## String Concatenation Output

```python
name = "Tom"
print("Hello " + name)
```

Output:
```
Hello Tom
```

⚠️ Note:
- `+` only works with strings
- Cannot mix string and number directly


## f-strings (Recommended)

```python
name = "Tom"
age = 23

print(f"My name is {name}, I am {age} years old.")
```

Output:
```
My name is Tom, I am 23 years old.
```

👉 This is the modern and most commonly used method.


## Input (user input)

### Basic usage

```python
name = input("Enter your name: ")
print(name)
```

Example:
```
Enter your name: Tom
Tom
```


## Important: input() returns STRING

```python
age = input("Enter age: ")
print(type(age))
```

Output:
```
<class 'str'>
```

👉 Even if you type a number, it is still a string.


## Type Conversion with Input

### Convert to integer

```python
age = int(input("Enter age: "))
print(age + 1)
```


### Convert to float

```python
height = float(input("Enter height: "))
print(height)
```


## Common Mistake

```python
age = input("Age: ")
print(age + 1)
```

❌ Error:
- You cannot add string + integer


## Correct Version

```python
age = int(input("Age: "))
print(age + 1)
```


## Real Example (Mini Program)

```python
name = input("Enter your name: ")
age = int(input("Enter your age: "))

print(f"Hello {name}")
print(f"You will be {age + 1} next year")
```


## Key Points Summary

- `print()` → output data
- `input()` → get user input
- `input()` always returns string
- Use `int()` / `float()` for conversion
- f-strings are the best way to format output


## Think Like a Program

```text
User → input() → process → print()
```

This is the basic structure of almost all programs.