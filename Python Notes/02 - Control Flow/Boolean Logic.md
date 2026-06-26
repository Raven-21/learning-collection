# Python Boolean Logic

## What is Boolean Logic?

Boolean logic is the system of working with only two values:

- `True`
- `False`

In programming, Boolean logic is used to make decisions.


## Basic Boolean Values

```python
is_active = True
is_logged_in = False
```


## Boolean in Conditions

Boolean values are often the result of comparisons:

```python
age = 20

print(age > 18)
```

Output:
```
True
```


## Comparison Produces Boolean

| Expression | Result |
|------------|--------|
| 5 > 3      | True   |
| 5 < 3      | False  |
| 5 == 5     | True   |
| 5 != 5     | False  |


## Logical Operators

Boolean logic becomes powerful when combined with logical operators.


### AND

```python
age = 20
has_id = True

print(age > 18 and has_id)
```

Meaning:
> Both conditions must be True


### OR

```python
is_weekend = True
is_holiday = False

print(is_weekend or is_holiday)
```

Meaning:
> At least one condition must be True


### NOT

```python
is_logged_in = False

print(not is_logged_in)
```

Meaning:
> Reverse the value


## Truth Table

### AND

| A | B | A and B |
|---|---|---------|
| True  | True  | True  |
| True  | False | False |
| False | True  | False |
| False | False | False |


### OR

| A | B | A or B |
|---|---|--------|
| True  | True  | True |
| True  | False | True |
| False | True  | True |
| False | False | False |


### NOT

| A | not A |
|---|-------|
| True  | False |
| False | True |


## Boolean in if Statements

Boolean logic is the core of `if` statements.

```python
age = 20

if age > 18:
    print("Adult")
```

👉 `age > 18` returns a Boolean value.


## Real Example

```python
age = 20
has_ticket = True

if age >= 18 and has_ticket:
    print("You can enter")
else:
    print("Access denied")
```


## Boolean Conversion

Any value can be converted to Boolean using `bool()`:

```python
print(bool(1))      # True
print(bool(0))      # False
print(bool("hi"))   # True
print(bool(""))     # False
```


## Falsy Values in Python

These values are considered False:

- `0`
- `0.0`
- `""` (empty string)
- `None`
- `[]` (empty list)

Everything else is usually True.


## Common Mistakes

### 1️⃣ Confusing = and ==

```python
if is_active = True   # ❌ wrong
```

Correct:

```python
if is_active == True
```

Better:

```python
if is_active:
```


### 2️⃣ Overcomplicating conditions

❌ Not recommended:

```python
if is_active == True:
```

✔ Better:

```python
if is_active:
```


## Key Ideas

- Boolean has only two values: True / False
- Comparisons return Boolean results
- `and`, `or`, `not` control logic
- Used everywhere in real programs
- Forms the foundation of decision-making


## Think Like a Program

```text
Condition → True / False → Decision → Action
```

Boolean logic is the “thinking system” of programming.