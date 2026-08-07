# 04 - JSON Persistence and Project Completion

The final stage of the To-Do List project focused on turning the application from an in-memory CRUD program into a persistent command-line application.

During this stage, I completed the interactive menu, task completion workflow, JSON persistence, data validation, and storage error handling. I also performed a final review of the overall project architecture.

## What I Implemented

The application now supports the complete task management workflow:

* Adding tasks.
* Viewing existing tasks.
* Updating task information.
* Deleting tasks.
* Marking tasks as complete.
* Automatically saving task data to JSON.
* Automatically restoring saved tasks when the application starts.
* Validating both user input and persisted task data.
* Handling invalid JSON and file I/O errors.

The final project structure separates responsibilities across several modules:

```text
main.py
task.py
task_manager.py
storage.py
ui.py
```

The application now runs through a continuous menu loop, while individual handler functions coordinate each user operation.

Task data is automatically persisted after operations that change application state.

## What I Learned

### 1. Serialization and Deserialization

One of the most important concepts I learned during this stage was how custom Python objects can be stored in JSON.

JSON cannot directly store a `Task` object, so the object must first be converted into JSON-compatible data.

The serialization process is:

```text
Task
    ↓
dict
    ↓
JSON
```

The reverse process is:

```text
JSON
    ↓
dict
    ↓
Task
```

I implemented `Task.to_dict()` to convert object state into a dictionary and `Task.from_dict()` to reconstruct a `Task` object from persisted data.

This helped me understand that persistence usually stores an object's state rather than the Python object itself.

### 2. Class Methods and Alternative Constructors

While implementing `Task.from_dict()`, I learned how `@classmethod` can provide an alternative way to create an object.

The normal constructor creates a task from individual arguments:

```python
Task(title, description)
```

The class method creates the same type of object from structured data:

```python
Task.from_dict(data)
```

This keeps the reconstruction logic inside the class that understands how a valid `Task` should be created.

### 3. Separating Persistence from Business Logic

I introduced `storage.py` to handle file operations separately from task management.

`TaskManager` does not know how tasks are stored on disk.

Instead:

* `Task` manages individual task state.
* `TaskManager` manages the task collection.
* `storage.py` handles persistence.
* Handler functions coordinate task operations and saving.
* `main.py` controls the application lifecycle.

This reinforced the idea that different kinds of responsibilities should remain separated even when they participate in the same workflow.

### 4. Validating External Data

I learned that data loaded from a file cannot automatically be trusted.

A JSON file can be syntactically valid while still containing data that does not match the requirements of the program.

The loading process therefore validates:

* Whether the top-level JSON structure is a list.
* Whether each task entry is a dictionary.
* Whether required fields exist.
* Whether field types are valid.
* Whether the stored task status is supported.

This introduced another form of defensive programming: validation is important not only for user input, but also for persisted external data.

### 5. Custom Exceptions and Exception Chaining

I created a custom `StorageError` exception to represent failures that belong to the persistence layer.

Low-level errors such as:

```text
JSONDecodeError
OSError
PermissionError
FileNotFoundError
```

do not need to be understood directly by the rest of the application.

Instead, storage-related failures can be translated into a project-level exception.

I also learned how:

```python
raise StorageError(...) from error
```

preserves the relationship between the original exception and the higher-level exception.

This allows the program to provide clearer error messages without losing the original technical cause during debugging.

## Design Decisions

Several important design decisions were made during the final stage:

* Tasks are automatically saved after operations that change application state.
* The application automatically loads saved tasks during startup.
* A missing data file represents an empty task list rather than an application error.
* Corrupted or invalid persisted data prevents the application from continuing with unreliable state.
* `Task` is responsible for changing its own status through `complete()`.
* `TaskManager` validates task indices before collection operations.
* Loaded task lists are copied when passed into `TaskManager`.
* Runtime task data is stored in `task_data.json` and excluded from version control.
* Storage-specific failures are represented by `StorageError`.

These decisions allow the command-line application to remain relatively simple while keeping responsibilities clearly separated.

## Reflection

This project marked an important step forward from simply learning Python syntax.

At the beginning of the project, the main focus was designing a valid `Task` object. As development continued, the project gradually expanded into a complete application involving object collaboration, CRUD operations, menu control flow, persistence, serialization, validation, and exception handling.

Compared with my first Python project, I spent more time thinking about questions such as:

* Which object should own a particular behavior?
* Which module should validate particular data?
* Where should user-facing concepts be converted into internal representations?
* Which parts of the application should know about persistence?
* How should low-level errors be exposed to higher layers?

I also became more comfortable refactoring code after functionality was working. Repeated logic was gradually extracted into handler and validation functions, while `main()` became responsible mainly for application flow.

The most important result of this project is not simply that I built a working To-Do List. It is that I gained more experience thinking about a program as a collection of cooperating components with separate responsibilities.

## Next Step

The To-Do List command-line application is now complete.

The remaining work is project documentation and final repository cleanup before moving on to the next Python project.

Future projects can build on the concepts practiced here:

* Object-oriented design.
* Separation of responsibilities.
* Serialization and persistence.
* Defensive validation.
* Exception abstraction.
* Multi-module application structure.