# Python Functions - Function Definition

## What is a Function?

A function is a reusable block of code that performs a specific task.

In simple words:

> “A function is a mini-program inside your program.”


## Why do we use functions?

Without functions:

```python
print("Hello Tom")
print("Hello Alice")
print("Hello Bob")
```

With functions:

```python
def say_hello():
    print("Hello")
```

👉 You can reuse the same logic many times.


## Function Definition Syntax

```python
def function_name():
    # code block
```


## Simple Function Example

```python
def greet():
    print("Hello World")
```

### Call the function:

```python
greet()
```

Output:
```
Hello World
```


## Function Workflow

```text
Define → Call → Execute
```

Example:

```python
def greet():
    print("Hi!")

greet()
```


## Function Naming Rules

### ✅ Good names:

```python
def say_hello():
def print_message():
def start_game():
```

### ❌ Bad names:

```python
def 123test():   # cannot start with number
def my-function():  # cannot use -
```


## Function Does NOT run automatically

```python
def test():
    print("Hello")
```

👉 Nothing happens until you call it:

```python
test()
```


## Function Reusability

```python
def greet():
    print("Hello!")

greet()
greet()
greet()
```

Output:
```
Hello!
Hello!
Hello!
```


## Function as a Program Block

You can think of a function as:

```text
Input (optional)
   ↓
Processing
   ↓
Output (optional)
```


## Real Example

```python
def show_menu():
    print("1. Start Game")
    print("2. Settings")
    print("3. Exit")

show_menu()
```


## Common Mistakes

### 1️⃣ Forgetting parentheses

```python
greet   # ❌ does nothing
greet() # ✔ correct
```


### 2️⃣ Forgetting indentation

```python
def test():
print("Hello")  # ❌ wrong
```

Correct:

```python
def test():
    print("Hello")
```


### 3️⃣ Defining but not calling

```python
def greet():
    print("Hi")

# nothing happens if not called
```


## Key Ideas

- Functions are reusable blocks of code
- Defined using `def`
- Must be called to run
- Help organize programs
- Improve readability and structure


## Think Like a Programmer

```text
Problem → Break into functions → Reuse blocks → Build program
```

Functions are the foundation of structured programming.