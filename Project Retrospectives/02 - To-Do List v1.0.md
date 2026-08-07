# To-Do List v1.0

## Introduction

I completed **To-Do List v1.0**, my second complete Python software project.

Unlike my first project, Guess the Number, this project was designed with object-oriented programming in mind from an early stage.

The project started with a simple `Task` object and gradually developed into a persistent command-line application with CRUD operations, task state management, JSON storage, data validation, and structured exception handling.

More importantly, this project gave me an opportunity to apply software engineering ideas that I had first encountered in my previous project instead of discovering all of them for the first time.


## Project Timeline

The project evolved through several stages.

```text
Task Object Design
        ↓
Constructor Validation
        ↓
TaskManager
        ↓
CRUD Operations
        ↓
Interactive Menu
        ↓
Handler Functions
        ↓
Task State Management
        ↓
Serialization & Deserialization
        ↓
JSON Persistence
        ↓
Storage Validation
        ↓
Custom Storage Exceptions
        ↓
Final Code Review
        ↓
Project Documentation
        ↓
To-Do List v1.0
```

Each stage introduced a different design problem.

The project gradually changed from a collection of task operations into a complete application with clear boundaries between objects, storage, user interaction, and application flow.


## Biggest Lessons

### Applying OOP from the Beginning

One of the biggest differences between this project and Guess the Number was how object-oriented programming was introduced.

In the first project, the program originally existed as procedural code and was later refactored into an object-oriented design.

In To-Do List, I started by asking what a `Task` object should represent and what responsibilities should belong to it.

For example:

- A `Task` validates its own title.
- A `Task` updates its own information.
- A `Task` changes its own completion status.
- `TaskManager` manages the collection of tasks.

This made object-oriented programming feel less like a syntax feature and more like a way of organizing responsibilities.


### Encapsulation Means Protecting Valid State

The `Task` class taught me that an object should not simply store arbitrary values.

Its constructor validates the title before assigning it, and invalid updates are rejected before the object's state changes.

This introduced a stronger idea of encapsulation:

> An object should help protect the validity of its own state.

Validation, normalization, and object behavior therefore became part of the design rather than being scattered throughout the user interface.


### Persistence Is More Than Writing a File

Before implementing JSON persistence, I initially thought of saving as simply writing data into a file.

Working with custom objects showed that the actual process is more involved.

```text
Task
    ↓
Dictionary
    ↓
JSON
```

Loading performs the reverse operation:

```text
JSON
    ↓
Dictionary
    ↓
Task
```

This helped me understand serialization and deserialization as transformations between runtime objects and persistent representations.

It also introduced `@classmethod` as an alternative constructor through `Task.from_dict()`.


### External Data Must Be Validated

Another important lesson was that successfully parsing JSON does not mean the data itself is valid.

A file can contain valid JSON syntax while still containing:

- The wrong top-level structure.
- Missing fields.
- Incorrect field types.
- Unsupported task states.

This made me think about file data in the same way as user input:

> Data entering the application from an external source should be validated before it is trusted.

This was an important step toward defensive programming.


### Exceptions Can Form Abstraction Boundaries

The storage layer introduced another idea that I had not fully appreciated before.

Low-level exceptions such as:

```text
JSONDecodeError
PermissionError
FileNotFoundError
OSError
```

describe implementation details of file and JSON operations.

The rest of the application does not need to understand all of these details.

By introducing `StorageError`, the storage layer can translate lower-level failures into an exception that represents the meaning of the problem at the application level.

I also learned how exception chaining preserves the original technical cause while providing a clearer higher-level error.

This showed me that exception handling is not only about preventing crashes. It can also be part of software architecture.


## Technical Milestones

During this project, I learned and practiced:

### Python

- Classes and objects
- Constructors
- Instance methods
- `@classmethod`
- Type hints
- `Optional`
- Lists of objects
- JSON
- File I/O
- Serialization and deserialization
- Exception handling
- Custom exceptions
- Exception chaining

### Object-Oriented Programming

- Object responsibilities
- Encapsulation
- Constructor validation
- State management
- Alternative constructors
- Object reconstruction
- Collection management

### Software Engineering

- CRUD design
- Separation of responsibilities
- Multi-module architecture
- Handler functions
- Input validation
- External data validation
- Persistence boundaries
- Error abstraction
- Defensive programming
- Refactoring
- Code review

The project also reinforced Git-based development through regular commits and incremental milestones.


## Architecture

The final application is divided into several components:

```text
main.py
    ↓
Handler Functions
    ↓
TaskManager
    ↓
Task

Handler Functions
    ↕
UI

Handler Functions
    ↕
Storage
    ↕
JSON
```

Each component has a specific responsibility:

- `Task` manages individual task state and validation.
- `TaskManager` manages the task collection.
- `ui.py` handles communication with the user.
- `storage.py` handles persistence and storage-related failures.
- Handler functions coordinate application operations.
- `main()` manages the application lifecycle and menu loop.

The architecture is still small, but it gave me useful practice thinking about how different components cooperate without taking over each other's responsibilities.


## Limitations and Possible Improvements

Version 1.0 intentionally remains a relatively small command-line application.

Possible future improvements could include:

- Reopening completed tasks.
- Adding stable task IDs instead of relying on list positions.
- Adding due dates or priorities.
- Searching or filtering tasks.
- Improving terminal presentation.
- Adding automated tests.
- Building a graphical or web-based interface.

I intentionally decided not to continue adding these features to version 1.0.

The purpose of this project was to practice object-oriented design, CRUD workflows, persistence, and error handling—not to turn a learning project into a permanently expanding application.

As with my first project, this reinforced an important principle:

> A project needs a clear definition of "done."


## Reflection

Guess the Number taught me how a simple program could gradually evolve through refactoring into a structured software project.

To-Do List felt different.

Instead of starting mainly from Python syntax and later discovering architecture, I began thinking about objects, responsibilities, validation, and module boundaries much earlier.

I also noticed that I was increasingly able to question design decisions myself.

Questions such as:

- Should this validation belong to `Task` or `TaskManager`?
- Should the UI know about list indices?
- Should persistence belong inside the manager?
- Should an invalid storage file be treated as an empty file?
- Should low-level storage exceptions escape into `main.py`?

became a normal part of development.

This change is important because it shows that my attention is gradually moving from:

> "How do I write this in Python?"

toward:

> "How should this program be designed?"

The project is still small, but the way I approached it was noticeably more structured than before.


## Looking Forward

With two complete Python projects finished, I now have experience with both basic program construction and small multi-module application design.

The next project should move further toward practical software while continuing to reinforce the same engineering principles.

I want future projects to introduce new technical areas without abandoning the habits developed here:

- Clear responsibilities.
- Small, understandable components.
- Validation at appropriate boundaries.
- Persistent data when necessary.
- Explicit error handling.
- Incremental development and refactoring.

The goal is no longer only to learn more Python syntax.

The goal is to gradually become capable of designing and building useful software independently.


## Final Thoughts

To-Do List v1.0 represents another step from learning individual programming concepts toward building complete applications.

Guess the Number taught me that working code can evolve into structured software.

To-Do List taught me how to begin with structure in mind and maintain that structure while adding features such as persistence and error handling.

The project is complete not because every possible feature has been added, but because it achieved the learning goals it was designed to achieve.

Version **1.0** marks the completion of Project 02 and the foundation for the next stage of my Python learning journey.