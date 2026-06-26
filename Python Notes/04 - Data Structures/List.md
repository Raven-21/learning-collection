# Python List

## What is a List?

A list is a data structure used to store multiple values in one variable.

In simple words:

> “A list is a container for storing many items.”

Example:

```python
numbers = [10, 20, 30]
```

Unlike normal variables, a list can store multiple values.


### 🧠 Variable vs List

Normal Variable - Stores only one value.


```python
age = 18
```

List - Stores multiple values.

```python
ages = [18, 20, 25]
```


## Creating a List

Lists are created using square brackets `[]`.

Example:

```python
fruits = ["apple", "banana", "orange"]
```

## List Can Store Different Types

Example:

```python
data = ["Tom", 23, 1.75, True]
```

A list can contain:
- strings
- integers
- floats
- booleans
- even other lists


## Accessing List Items

Lists use indexes.

```python
fruits = ["apple", "banana", "orange"]
```

First Element

```python
print(fruits[0])
```

Output:
```text
apple
```

## Index Starts from 0

⚠️ Index positions begin at 0, not 1.

| Index | Value |
|---|---|
| 0 | apple |
| 1 | banana |
| 2 | orange |


## Negative Index

Negative indexes access from the end.

Example:

```python
fruits = ["apple", "banana", "orange"]

print(fruits[-1])
```

Output:
```text
orange
```

### 🧠 Why Useful?

The latest data is often stored at the end of a list.

Very common in real software development.


## Modifying List Items

Example:

```python
fruits = ["apple", "banana", "orange"]

fruits[1] = "grape"

print(fruits)
```

Output:
```text
['apple', 'grape', 'orange']
```


## Adding Items

### `append()` - Adds a new element to the end of a list.

Example:

```python
numbers = [1, 2, 3]

numbers.append(4)

print(numbers)
```

Output:
```text
[1, 2, 3, 4]
```

### 🧠 Common Real-World Pattern

```text
Loop
↓
Collect data
↓
Append into list
```


## Removing Items

### `remove()` - Remove by Value

```python
fruits = ["apple", "banana", "orange"]

fruits.remove("banana")

print(fruits)
```

Output:
```text
["apple", "orange"]
```


### `pop()` - Removes by index


```python
numbers = [1, 2, 3]

numbers.pop(1)

print(numbers)
```

Output:
```text
[1, 3]
```

👉 Removes the last element

```python
history.pop()
```

Commonly used for:

- Undo systems
- Backtracking
- Stack structures


## List Length

### `len()` - Returns the number of elements in the list


Example:

```python
numbers = [1, 2, 3]

print(len(numbers))
```

Output:
```text
3
```


## Looping Through a List

### for loop

Example:

```python
fruits = ["apple", "banana", "orange"]

for fruit in fruits:
    print(fruit)
```

Output:
```text
apple
banana
orange
```


## Checking Membership

### `in` - Checks whether a value exists in the list

Example 1:

```python
fruits = ["apple", "banana"]

print("apple" in fruits)
```

Output:
```text
True
```

Example 2:

```python
if 50 in history:
    print("Found!")
```


## Empty List

```python
history = []
```

Often used for collecting data dynamically.


## Dynamic Data Collection

```python
numbers = []

numbers.append(10)
numbers.append(20)

print(numbers)
```

Output:
```text
[10, 20]
```


## Real Example

```python
guess_history = []

guess_history.append(30)
guess_history.append(50)

print(guess_history)
```

This is similar to your guessing game history system.


## Nested Lists

Lists can contain other lists.

```python
matrix = [
    [1, 2],
    [3, 4]
]
```


## Common Beginner Mistakes

### 1️⃣ Index out of range

```python
numbers = [1, 2, 3]

print(numbers[5])
```

❌ Error:
```text
IndexError
```


### 2️⃣ Forgetting parentheses

```python
numbers.append
```

❌ Does not run

Correct:

```python
numbers.append(4)
```


### 3️⃣ Using wrong index

Remember:
- first index = `0`
- last index = `-1`


## Common List Methods

| Method | Purpose |
|---|---|
| `append()` | add item |
| `remove()` | remove item by value |
| `pop()` | remove item by index |
| `len()` | get length |


## Why Lists Are Important

Lists are one of the most important data structures in programming.

They are used for:
- storing collections
- processing data
- loops
- AI datasets
- web applications
- game systems

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


## Think Like a Programmer

```text
Single variable → stores one value
List → stores many values
```

Lists help programs manage collections of data efficiently.


## Key Ideas

- lists store multiple items
- indexes access data
- lists are mutable (modifiable)
- append/remove manage dynamic data
- essential for real programming


## Final Summary

```text
Lists are flexible containers that allow programs
to store, organize, and process multiple pieces of data.
```