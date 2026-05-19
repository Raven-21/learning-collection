# Python List Note

## 1️⃣ What is a List?

A list is used to store a group of data.

Example:

```python
numbers = [10, 20, 30]
```

Unlike normal variables, a list can store multiple values.


## 🧠 Variable vs List

### Normal Variable

```python
age = 18
```

Stores only one value.

### List

```python
ages = [18, 20, 25]
```

Stores multiple values.


# 2️⃣ Creating Lists

## Empty List

```python
history = []
```

Commonly used for dynamically adding data later.


## List with Initial Values

```python
numbers = [1, 2, 3]
```


## Mixed Data Types

Python lists can store different types of data.

```python
data = [1, "hello", True]
```

Although possible, keeping consistent data types is usually better.


# 3️⃣ append() — Most Important Method

`append()` adds a new element to the end of a list.

Example:

```python
history = []

history.append(30)
history.append(50)

print(history)
```

Output:

```python
[30, 50]
```


## 🧠 Common Real-World Pattern

```text
Loop
↓
Collect data
↓
Append into list
```

This is extremely common in real applications.


# 4️⃣ Accessing Elements (Indexing)

Example:

```python
numbers = [10, 20, 30]
```


## First Element

```python
numbers[0]
```

Result:

```python
10
```


## Second Element

```python
numbers[1]
```

Result:

```python
20
```


# ⚠️ Python Starts from 0

Index positions begin at 0, not 1.


# 5️⃣ Negative Indexing

## Last Element

```python
history[-1]
```

Example:

```python
history = [30, 50, 42]

print(history[-1])
```

Output:

```python
42
```


## 🧠 Why Useful?

The latest data is often stored at the end of a list.

Very common in real software development.


# 6️⃣ len() — Length of a List

```python
len(history)
```

Returns the number of elements in the list.

Example:

```python
history = [30, 50, 42]

print(len(history))
```

Output:

```python
3
```


# 7️⃣ for Loop Traversal

A standard way to read all elements in a list.

Example:

```python
history = [30, 50, 42]

for guess in history:
    print(guess)
```

Output:

```python
30
50
42
```


# 8️⃣ in — Membership Check

```python
if 50 in history:
    print("Found!")
```

Checks whether a value exists in the list.


# 9️⃣ remove() — Remove by Value

```python
numbers = [10, 20, 30]

numbers.remove(20)

print(numbers)
```

Output:

```python
[10, 30]
```


# 🔟 pop() — Remove Last Element

```python
history.pop()
```

Removes the last element.

Commonly used for:

- Undo systems
- Backtracking
- Stack structures


# 1️⃣1️⃣ Understanding Lists Conceptually

A list is not just “many variables”.

It is:

# 👉 An ordered data container

Example:

```python
history = [30, 50, 42]
```

Conceptually:

```text
Index 0 → 30
Index 1 → 50
Index 2 → 42
```


# 🧠 Important Concepts Learned

## Current Core Skills

### Basic List Skills
- `[]`
- `append()`
- `len()`
- Indexing

### Next Important Skills
- `for item in list`
- Negative indexing (`[-1]`)
- Combining list with dictionary

### Future Topics
- List slicing
- List comprehension
- Nested lists


# 🚀 Why Lists Matter

Lists are one of the most important data structures in Python.

Real software often works like this:

```text
Data
↓
Structured storage
↓
Processing
↓
Display
```

Learning lists is the beginning of understanding real program data management.