# Python for Loop

## What is a for Loop?

A `for` loop is used to iterate over a sequence.

In simple words:

> “Go through each item one by one.”


## Basic Structure

```python
for item in sequence:
    # do something
```


## Looping through a List

```python
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
```

Output:
```
apple
banana
cherry
```


## Looping through a String

```python
for char in "hello":
    print(char)
```

Output:
```
h
e
l
l
o
```


## range() Function

Used to generate a sequence of numbers.

### Example 1:

```python
for i in range(5):
    print(i)
```

Output:
```
0
1
2
3
4
```


### Example 2 (start and end):

```python
for i in range(1, 6):
    print(i)
```

Output:
```
1
2
3
4
5
```


### Example 3 (step):

```python
for i in range(0, 10, 2):
    print(i)
```

Output:
```
0
2
4
6
8
```


## for vs while

| for loop | while loop |
|----------|------------|
| fixed sequence | condition-based |
| easier to read | more flexible |
| best for lists/ranges | best for unknown repetition |


## Using break in for loop

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

Output:
```
0
1
2
3
4
```


## Using continue

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

Output:
```
0
1
3
4
```


## Nested for Loops

```python
for i in range(3):
    for j in range(2):
        print(i, j)
```

Output:
```
0 0
0 1
1 0
1 1
2 0
2 1
```


## Real Example: Simple Table

```python
for i in range(1, 6):
    print(f"2 x {i} = {2 * i}")
```

Output:
```
2 x 1 = 2
2 x 2 = 4
2 x 3 = 6
2 x 4 = 8
2 x 5 = 10
```


## Looping with index (enumerate)

```python
fruits = ["apple", "banana", "cherry"]

for index, fruit in enumerate(fruits):
    print(index, fruit)
```

Output:
```
0 apple
1 banana
2 cherry
```


## Common Mistakes

### 1️⃣ Wrong indentation

```python
for i in range(5):
print(i)  # ❌ wrong
```


### 2️⃣ Forgetting range

```python
for i in 5:  # ❌ wrong
```

Correct:

```python
for i in range(5):
```


### 3️⃣ Confusing for and while

- for = known number of loops
- while = condition-based loops


## Key Ideas

- for loops iterate over sequences
- range() generates numbers
- useful for lists, strings, numbers
- easier than while in many cases
- very common in real programming


## Think Like a Program

```text
Take sequence → one item at a time → process → next
```

for loop = structured repetition