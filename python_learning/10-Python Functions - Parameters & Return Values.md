# Python Functions - Parameters & Return Values

## 1. What are Parameters and Return Values?

Functions can:

- **receive data (parameters)**
- **send back results (return values)**

In simple words:

> Parameters = input to the function  
> Return = output from the function


## 2. Function without parameters

```python
def greet():
    print("Hello")
```

Call:

```python
greet()
```

👉 No input needed


## 3. Function with parameters

Parameters allow you to pass data into a function.

```python
def greet(name):
    print("Hello", name)
```

Call:

```python
greet("Tom")
greet("Alice")
```

Output:
```
Hello Tom
Hello Alice
```


## 4. Multiple parameters

```python
def add(a, b):
    print(a + b)
```

Call:

```python
add(3, 5)
```

Output:
```
8
```


## 5. Parameters vs Arguments

| Term | Meaning |
|------|--------|
| Parameter | variable in function definition |
| Argument | actual value passed in |

Example:

```python
def greet(name):   # parameter
    print(name)

greet("Tom")       # argument
```


## 6. What is return?

`return` sends a result back from a function.


## 7. Function with return value

```python
def add(a, b):
    return a + b
```

Usage:

```python
result = add(3, 5)
print(result)
```

Output:
```
8
```


## 8. Why return is important

Without return:

```python
def add(a, b):
    print(a + b)
```

You cannot reuse the result.

With return:

```python
result = add(3, 5)
```

👉 You can store and reuse the value.


## 9. return stops the function

```python
def test():
    return "Hello"
    print("This will NOT run")
```

👉 Code after return is ignored.


## 10. Multiple return paths

```python
def check_age(age):
    if age >= 18:
        return "Adult"
    else:
        return "Minor"
```


## 11. Function flow with return

```text
Input → Process → Return Output
```

Example:

```python
def square(x):
    return x * x
```


## 12. Real Example

```python
def calculate_total(price, tax):
    return price + tax

total = calculate_total(100, 20)
print(total)
```

Output:
```
120
```


## 13. Common Mistakes

### 1. Forgetting return

```python
def add(a, b):
    a + b   # ❌ no return
```


### 2. Using print instead of return

```python
def add(a, b):
    print(a + b)
```

👉 Not reusable in calculations


### 3. Ignoring return value

```python
def add(a, b):
    return a + b

add(3, 5)  # ❌ result lost
```


## 14. Default Parameters (Extra)

```python
def greet(name="Guest"):
    print("Hello", name)
```

Call:

```python
greet()
greet("Tom")
```


## 15. Key Ideas

- Parameters = input to function
- Return = output from function
- return allows reuse of results
- return stops function execution
- Functions become powerful when using both


## 16. Think Like a Program

```text
Input → Function → Output → Reuse
```

This is the core model of all real software systems.


## 17. Real Usage in My Projects

I already use this in:

- `check_guess()` → returns result
- `get_guess()` → returns user input
- `choose_difficulty()` → returns attempt count
- game logic functions → return game state

👉 This is a major step toward real software architecture.