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


## Summary

* JSON is a lightweight text format for structured data.
* A Python dictionary and JSON look similar but are different.
* `json.dumps()` converts a dictionary into a JSON string.
* `json.loads()` converts a JSON string back into a dictionary.
* `json.dump()` writes structured data directly into a JSON file.
* `json.load()` reads JSON files into structured data directly.
* JSON is commonly used for data storage, configuration files, and Web APIs.