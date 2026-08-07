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

| Python Dictionary | JSON |
| --- | --- |
| Python object | Text format |
| Exists in Python memory | Can be stored or transmitted as text |
| Supports Python data types | Supports JSON-compatible data types |
| May use single or double quotes for strings | Requires double quotes for strings |


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

`json.dumps()` serializes a JSON-compatible Python object into a JSON string.


### JSON String → Dictionary

```python
new_person = json.loads(text)
```

`json.loads()` deserializes a JSON string into the corresponding Python data structure.


## Working with JSON Files

JSON data can be written directly to a file.

```python
import json

settings = {
    "theme": "dark",
    "language": "en"
}

with open("settings.json", "w", encoding="utf-8") as file:
    json.dump(settings, file, indent=4, ensure_ascii=False)
```

The resulting file contains structured data in a human-readable text format.


## Reading JSON Files

JSON data can be read from a file using `json.load()`.

```python
import json

with open("settings.json", "r", encoding="utf-8") as file:
    settings = json.load(file)

print(settings)
print(type(settings))
```

A JSON object is normally loaded as a Python dictionary.

For example:

```json
{
    "theme": "dark"
}
```

becomes:

```python
{
    "theme": "dark"
}
```


## dump() vs load()

| Function | Purpose |
| --- | --- |
| `json.dump()` | Serialize Python data into a JSON file |
| `json.load()` | Deserialize JSON data from a file |
| `json.dumps()` | Serialize Python data into a JSON string |
| `json.loads()` | Deserialize a JSON string into Python data |


## Serialization and Deserialization

### Serialization

Serialization converts program data into a format that can be stored or transmitted.

With the `json` module:

```python
json.dump(data, file)
```

or:

```python
json.dumps(data)
```

can serialize JSON-compatible Python data.


### Deserialization

Deserialization reconstructs program data from its stored representation.

```python
json.load(file)
```

or:

```python
json.loads(text)
```

converts JSON data back into Python data structures.

The general process is:

```text
Python Data
    ↓
Serialization
    ↓
JSON
    ↓
Deserialization
    ↓
Python Data
```


## Custom Objects and JSON

Instances of custom classes cannot normally be passed directly to `json.dump()`.

For example:

```python
class User:
    def __init__(self, name: str, email: str) -> None:
        self.name = name
        self.email = email


user = User("Alice", "alice@example.com")
```

This does not work directly:

```python
json.dump(user, file)
```

because the JSON encoder does not know how to represent a `User` object.

A common solution is to convert the object into JSON-compatible data first.

```python
class User:
    def __init__(self, name: str, email: str) -> None:
        self.name = name
        self.email = email

    def to_dict(self) -> dict:
        return {
            "name": self.name,
            "email": self.email,
        }
```

The object can then be serialized:

```python
data = user.to_dict()

with open("user.json", "w", encoding="utf-8") as file:
    json.dump(data, file, indent=4)
```

The process is:

```text
Custom Object
    ↓
dict
    ↓
JSON
```


## Reconstructing Custom Objects

When JSON is loaded, it produces ordinary Python data structures rather than instances of custom classes.

For example:

```python
with open("user.json", "r", encoding="utf-8") as file:
    data = json.load(file)
```

`data` is a dictionary, not a `User` object.

A class method can be used as an alternative constructor:

```python
class User:
    def __init__(self, name: str, email: str) -> None:
        self.name = name
        self.email = email

    @classmethod
    def from_dict(cls, data: dict) -> "User":
        return cls(
            data["name"],
            data["email"],
        )
```

The object can then be reconstructed:

```python
user = User.from_dict(data)
```

The complete round trip is:

```text
Custom Object
    ↓
to_dict()
    ↓
dict
    ↓
JSON
    ↓
dict
    ↓
from_dict()
    ↓
Custom Object
```

JSON stores the object's data, not its methods or class behavior.

The program reconstructs the object from the stored data when it is loaded.


## Validating Loaded JSON Data

Valid JSON is not necessarily valid application data.

For example, this is syntactically valid JSON:

```json
{
    "age": "unknown"
}
```

but an application may require `age` to be an integer.

`JSONDecodeError` only tells us whether the JSON syntax is valid. Applications should separately validate the structure and values of loaded data.

For example:

```python
if not isinstance(data, dict):
    raise ValueError("Data must be a dictionary.")

if "name" not in data:
    raise ValueError("Name is required.")
```

Validation is especially important when JSON data is used to reconstruct custom objects.


## Common JSON Exceptions

Invalid JSON syntax raises `json.JSONDecodeError`.

```python
import json

try:
    with open("data.json", "r", encoding="utf-8") as file:
        data = json.load(file)

except json.JSONDecodeError:
    print("Invalid JSON format.")
```

For example, malformed JSON such as:

```json
{
    "name": "Alice"
```

cannot be decoded successfully.

File operations may also raise file system exceptions such as `OSError` or its subclasses. These are file I/O problems rather than JSON syntax problems.


## Persistence Design

When JSON is used for persistence, store the data required to reconstruct application state.

Data that can be reliably calculated from other stored values often does not need to be stored separately.

This reduces unnecessary duplication and prevents stored values from becoming inconsistent with each other.

A typical persistence flow is:

```text
Application State
    ↓
Convert to JSON-compatible data
    ↓
Serialize
    ↓
JSON File
    ↓
Deserialize
    ↓
Validate
    ↓
Reconstruct application state
```


## Best Practices

* Use JSON for structured, portable text data.
* Remember that custom Python objects are not directly JSON serializable by default.
* Convert custom objects into JSON-compatible structures before serialization.
* Validate data after loading it from external storage.
* Treat JSON syntax validation and application data validation as separate concerns.
* Handle `JSONDecodeError` when reading JSON data.
* Handle file I/O errors separately from JSON parsing errors.
* Store the state required to reconstruct the application rather than unnecessary derived values.