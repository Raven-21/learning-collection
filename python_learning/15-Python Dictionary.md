# Python Dictionary (dict)

## 1. What is a Dictionary?

A dictionary is a data structure that stores data in **key-value pairs**.

In simple words:

> “A dictionary is like a real-world dictionary: you look up a word (key) to get its meaning (value).”


## 2. Creating a Dictionary

Dictionaries use curly braces `{}`.

```python
student = {
    "name": "Tom",
    "age": 18,
    "grade": "A"
}
```


## 3. Key-Value Concept

Each item has:

- **Key** → the identifier
- **Value** → the data

Example:

```text
"name" → "Tom"
"age" → 18
```


## 4. Accessing Values

```python
student = {
    "name": "Tom",
    "age": 18
}

print(student["name"])
```

Output:
```text
Tom
```


## 5. Adding / Updating Values

### Add new key

```python
student["score"] = 95
```

### Update existing key

```python
student["age"] = 19
```


## 6. Removing Items

### pop()

```python
student = {
    "name": "Tom",
    "age": 18
}

student.pop("age")
```


## 7. Checking Keys

### in

```python
student = {
    "name": "Tom"
}

print("name" in student)
```

Output:
```text
True
```


## 8. Getting Keys Safely

### get()

Avoids errors if key does not exist.

```python
student = {
    "name": "Tom"
}

print(student.get("age"))
```

Output:
```text
None
```


## 9. Looping Through Dictionary

### Keys

```python
student = {
    "name": "Tom",
    "age": 18
}

for key in student:
    print(key)
```


### Values

```python
for value in student.values():
    print(value)
```


### Key + Value

```python
for key, value in student.items():
    print(key, value)
```


## 10. Dictionary Length

```python
student = {
    "name": "Tom",
    "age": 18
}

print(len(student))
```

Output:
```text
2
```


## 11. Empty Dictionary

```python
data = {}
```

Used when data will be added later dynamically.


## 12. Nested Dictionary

```python
student = {
    "name": "Tom",
    "grades": {
        "math": 90,
        "english": 85
    }
}
```

Access nested value:

```python
print(student["grades"]["math"])
```


## 13. Real Example: Game History

You already used this idea in your project:

```python
history = []

history.append({
    "guess": 50,
    "result": "high"
})
```

Each record is a dictionary.


## 14. Dictionary vs List

| Feature | List | Dictionary |
|---|---|---|
| Structure | ordered values | key-value pairs |
| Access | index [0] | key ["name"] |
| Meaning | sequence | labeled data |


## 15. When to Use Dictionary

Use dict when:

- data has meaning (name, age, score)
- you need labels
- structure matters
- representing objects or records


## 16. Common Beginner Mistakes

### 1️⃣ Key error

```python
student = {"name": "Tom"}

print(student["age"])  # ❌ error
```


### 2️⃣ Forgetting quotes for keys

```python
student = {
    name: "Tom"  # ❌ wrong
}
```

Correct:

```python
student = {
    "name": "Tom"
}
```


### 3️⃣ Confusing list and dict

```python
# list
[1, 2, 3]

# dict
{"a": 1, "b": 2}
```


## 17. Common Dictionary Methods

| Method | Purpose |
|---|---|
| `get()` | safe access |
| `keys()` | get all keys |
| `values()` | get all values |
| `items()` | get key-value pairs |
| `pop()` | remove item |


## 18. Why Dictionary Is Important

Dictionaries are used everywhere in programming:

- user profiles
- API responses (JSON)
- databases
- game state
- configuration files


## 19. Think Like a Programmer

```text
List → index-based storage
Dictionary → meaning-based storage
```

Dictionary helps organize structured data clearly.


## 20. Real Usage in Your Projects

You already use dictionaries in:

- guess history system:
  ```python
  {"guess": guess, "result": result}
  ```

- structured game records
- future statistics system


## 21. Key Ideas

- dictionary = key-value storage
- keys are unique
- values can be any type
- used for structured data
- essential for real-world programming


## 22. Final Summary

```text
Dictionaries allow programs to store data in a structured,
meaningful way using key-value pairs.
```