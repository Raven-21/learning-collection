# JSON

## What is JSON?

JSON (JavaScript Object Notation) is a lightweight text format used to store and exchange structured data.

Although JSON was originally created for JavaScript, it is now supported by almost every programming language.

Common uses of JSON include:

* Saving application data
* Configuration files
* Web APIs
* Data exchange between programs


## Python Dictionary vs JSON

A Python dictionary is an object stored in memory.

```python
person = {
    "name": "Tom",
    "age": 20
}
```

JSON is a text representation of structured data.

```json
{
    "name": "Tom",
    "age": 20
}
```

Although they look very similar, they are different.

| Python Dictionary                      | JSON                                |
| -------------------------------------- | ----------------------------------- |
| Python object                          | Text format                         |
| Stored in memory                       | Stored as text                      |
| Single quotes when displayed by Python | Uses double quotes by specification |


## Converting Between Dictionary and JSON

### Dictionary → JSON String

```python
import json

person = {
    "name": "Tom",
    "age": 20
}

text = json.dumps(person)
```

`json.dumps()` converts a Python dictionary into a JSON string.


### JSON String → Dictionary

```python
new_person = json.loads(text)
```

`json.loads()` converts a JSON string back into a Python dictionary.


## Working with JSON Files

JSON can also be written directly into a file.

```python
import json

data = {
    "number": game.number,
    "my_list": game.my_list
}

with open("ObjRecords.json", "w", encoding="utf-8") as file:
    json.dump(data, file, indent=4)
```

This creates a JSON file that stores structured data instead of plain text.

## Reading JSON Files

JSON data can also be read directly from a file.

```python
import json

with open("ObjRecords.json", "r", encoding="utf-8") as file:
    data = json.load(file)

print(data)
print(type(data))
```

`json.load()` reads JSON data from a file and converts it into a Python object.

For example, a JSON object becomes a Python dictionary.


## dump() vs load()

| Function      | Purpose                                |
| ------------- | -------------------------------------- |
| `json.dump()` | Write a Python object into a JSON file |
| `json.load()` | Read a JSON file into a Python object  |


## Serialization & Deserialization

Two important concepts when working with JSON are:

### Serialization

Convert a Python object into JSON.

Examples:

```python
json.dump(data, file)
```

or

```python
json.dumps(data)
```

### Deserialization

Convert JSON back into a Python object.

Examples:

```python
json.load(file)
```

or

```python
json.loads(text)
```

Serialization allows programs to save structured data.

Deserialization allows programs to restore that data later.


## Common JSON Exceptions

Reading JSON files may raise exceptions.

Example:

```python
import json

try:
    with open("data.json", "r", encoding="utf-8") as file:
        data = json.load(file)

except json.JSONDecodeError:
    print("Invalid JSON format.")
```

`JSONDecodeError` occurs when the file exists but its contents are not valid JSON.

Programs should handle this exception to improve reliability.


## JSON and Project Design

In the Guess the Number project, JSON is used to save the game's raw state.

Example:

```json
{
    "number": 34,
    "max_chance": 10,
    "history": [
        {
            "guess": 50,
            "result": "high"
        },
        {
            "guess": 34,
            "result": "correct"
        }
    ]
}
```

Raw state such as:

* number
* max_chance
* history

should be stored.

Derived state such as:

* remaining_chance
* is_first_try

does not need to be stored because it can be calculated from the raw state.


## Best Practices

- Use JSON to store structured data instead of plain text.
- Store raw state instead of derived state whenever possible.
- Use `json.dump()` and `json.load()` when working with files.
- Handle `JSONDecodeError` when reading JSON files.