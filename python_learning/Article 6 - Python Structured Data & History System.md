# 🧠 Python Structured Data & History System

## 🎯 Core Goal

Upgrade the guessing game from:

```python
history = [30, 50, 42]
```

to:

```python
history = [
    {"guess": 30, "result": "low"},
    {"guess": 50, "result": "high"},
    {"guess": 42, "result": "correct"}
]
```

This is the beginning of working with structured data.


# 1️⃣ What is Structured Data?

Instead of storing only raw values:

```python
[30, 50, 42]
```

we store information with meaning:

```python
{
    "guess": 30,
    "result": "low"
}
```

This structure is called a:

- record
- object
- structured data


# 2️⃣ What is a Dictionary (dict)?

A dictionary stores data as:

```text
key → value
```

Example:

```python
record = {
    "guess": 30,
    "result": "low"
}
```


## 🧠 Keys

```python
"guess"
"result"
```


## 🧠 Values

```python
30
"low"
```


# 3️⃣ Accessing Dictionary Values

Use square brackets with keys.

Example:

```python
record["guess"]
```

Output:

```python
30
```


Another example:

```python
record["result"]
```

Output:

```python
"low"
```


# 4️⃣ List + Dictionary Combination

This is one of the most important data structures in Python.

Example:

```python
history = [
    {"guess": 30, "result": "low"},
    {"guess": 50, "result": "high"},
    {"guess": 42, "result": "correct"}
]
```


# 🧠 Conceptual Understanding

## List

Stores:

```text
multiple items
```


## Dictionary

Stores:

```text
information about one item
```


## List + Dictionary

Stores:

```text
multiple objects with structured information
```


# 5️⃣ Recording Structured History

Old version:

```python
history.append(guess)
```

Only stores numbers.


New version:

```python
history.append({
    "guess": guess,
    "result": result
})
```

Now each record contains:

- the guessed number
- the guess result


# 6️⃣ Traversing Structured Data

Use a `for` loop.

Example:

```python
for record in history:
    print(record)
```

Each loop gets one dictionary.


# 🧠 Example

First iteration:

```python
record = {"guess": 30, "result": "low"}
```

Second iteration:

```python
record = {"guess": 50, "result": "high"}
```


# 7️⃣ Building a History Viewer

Example:

```python
def show_history(history):

    print("\nGuess History:")

    for record in history:

        print(
            f"{record['guess']} → {record['result']}"
        )
```


# 🧠 How It Works

## Step 1

Loop through history:

```python
for record in history:
```


## Step 2

Extract dictionary values:

```python
record["guess"]
record["result"]
```


## Step 3

Display formatted output:

```python
f"{record['guess']} → {record['result']}"
```


# 8️⃣ Why This Is Important

This is the foundation of:

- backend development
- APIs
- JSON data
- databases
- AI data processing
- game systems
- analytics systems


# 9️⃣ Software Design Concepts Learned

## Separation of Concerns

### Logic Layer

Responsible for:

```python
return "high"
return "low"
return "correct"
```


### Presentation Layer

Responsible for:

```python
print()
show_history()
show_result()
```


## Benefits

- Cleaner architecture
- Easier debugging
- Easier feature expansion
- Better code readability
- Lower coupling


# 🔟 Program State Thinking

The game now works like this:

```text
User Input
↓
Logic Processing
↓
Result State
↓
Structured Data Recording
↓
Presentation Layer Display
```

This is a major step toward real software architecture.


# 🚀 Key Concepts Learned

## Python Data Structures
- list
- dictionary (dict)

## Data Processing
- structured records
- data traversal
- state management

## Software Design
- layered architecture
- separation of logic and UI
- presentation abstraction
- structured history systems