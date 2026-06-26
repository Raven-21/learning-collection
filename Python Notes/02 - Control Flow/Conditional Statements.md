# Python Conditional Statements

## What is Conditional Logic?

Conditional statements allow a program to make decisions.

In simple words:

> “If something is true, do this. Otherwise, do something else.”


## Basic Structure

```python
if condition:
    # do something
```


## if Statement

```python
age = 18

if age >= 18:
    print("You are an adult")
```

Output:
```
You are an adult
```


## if + else

```python
age = 16

if age >= 18:
    print("Adult")
else:
    print("Minor")
```

Output:
```
Minor
```


## if + elif + else

Used when there are multiple conditions.

```python
score = 85

if score >= 90:
    print("A")
elif score >= 80:
    print("B")
elif score >= 70:
    print("C")
else:
    print("F")
```


## Comparison Operators

| Operator | Meaning | Example |
|----------|--------|--------|
| `==` | equal | a == b |
| `!=` | not equal | a != b |
| `>` | greater than | a > b |
| `<` | less than | a < b |
| `>=` | greater or equal | a >= b |
| `<=` | less or equal | a <= b |


## Logical Operators

Used to combine conditions.

### and

```python
age = 20

if age > 18 and age < 30:
    print("Young adult")
```

### or

```python
age = 15

if age < 18 or age > 60:
    print("Special group")
```

### not

```python
is_student = False

if not is_student:
    print("Not a student")
```


## Indentation (Very Important)

Python uses indentation to define code blocks.

```python
if True:
    print("This is inside if")
```

❌ Wrong:

```python
if True:
print("Error")  # no indentation
```


## Nested if

```python
age = 20

if age >= 18:
    if age < 60:
        print("Working age")
```


## Real Example

```python
age = int(input("Enter age: "))

if age >= 18:
    print("You can drive")
else:
    print("You cannot drive yet")
```


## Common Mistakes

### 1️⃣ Using = instead of ==

```python
if age = 18:   # ❌ wrong
```

Correct:

```python
if age == 18:
```


### 2️⃣ Forgetting colon :

```python
if age > 18   # ❌ missing :
```


### 3️⃣ Wrong indentation

Python will throw an error.


## Key Ideas

- `if` is for decision making
- `elif` adds multiple conditions
- `else` is fallback
- indentation defines structure
- comparison + logic operators are essential


## Think Like a Program

```text
Input → Condition → Decision → Output
```

Conditional logic is the foundation of all program behavior.