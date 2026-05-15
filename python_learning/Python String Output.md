# Python String Output Notes

In Python, `print()` automatically adds a space between multiple arguments.

Example:

```python
name = "Tom"
print("Hello", name)
```

Output:

```text
Hello Tom
```

This happens because `print()` separates arguments with spaces by default.


## Method 1: String Concatenation

You can use `+` to combine strings.

```python
name = "Tom"
print("Hello" + name)
```

Output:

```text
HelloTom
```

However, `+` only works with strings.

```python
age = 23
print("Age: " + age)
```

This causes an error because:
- `"Age: "` is a string
- `23` is an integer

To fix this, convert the integer using `str()`:

```python
age = 23
print("Age: " + str(age))
```

## Method 2: f-strings (Recommended)

f-strings are the modern and most commonly used way to format strings in Python.

```python
name = "Tom"
print(f"Hello{name}")
```

They are especially useful when working with multiple variables.

```python
name = "Tom"
age = 23

print(f"My name is {name}, and I am {age} years old.")
```

Output:

```text
My name is Tom, and I am 23 years old.
```

## Why f-strings Matter

f-strings are widely used in:
- Project development
- AI applications
- Automation scripts

Learning them early is very helpful.

This is also an introduction to string handling, which is a very important part of programming.