# Python Functions - Function Definition

## 1. What is a Function?

A function is a reusable block of code that performs a specific task.

In simple words:

> “A function is a mini-program inside your program.”


## 2. Why do we use functions?

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


## 3. Function Definition Syntax

```python
def function_name():
    # code block
```


## 4. Simple Function Example

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


## 5. Function Workflow

```text
Define → Call → Execute
```

Example:

```python
def greet():
    print("Hi!")

greet()
```


## 6. Function Naming Rules

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


## 7. Function Does NOT run automatically

```python
def test():
    print("Hello")
```

👉 Nothing happens until you call it:

```python
test()
```


## 8. Function Reusability

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


## 9. Function as a Program Block

You can think of a function as:

```text
Input (optional)
   ↓
Processing
   ↓
Output (optional)
```


## 10. Real Example

```python
def show_menu():
    print("1. Start Game")
    print("2. Settings")
    print("3. Exit")

show_menu()
```


## 11. Common Mistakes

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


## 12. Key Ideas

- Functions are reusable blocks of code
- Defined using `def`
- Must be called to run
- Help organize programs
- Improve readability and structure


## 13. Think Like a Programmer

```text
Problem → Break into functions → Reuse blocks → Build program
```

Functions are the foundation of structured programming.


## 14. Real Usage in My Projects

I already use functions in:

- Guess number game structure
- Input handling (`get_guess`)
- Game loop (`play_game`)
- UI display (`show_count`, `show_game_over`)

👉 I are already writing modular programs like a real developer.