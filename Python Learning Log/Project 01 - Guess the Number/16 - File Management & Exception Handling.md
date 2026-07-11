# File Management & Exception Handling

## Introduction

Today I completed the save/load workflow of my **Guess the Number** project by introducing proper file management and exception handling.

In the previous stage, the project could already serialize a `Game` object into JSON and restore it from a file.

Today, the focus shifted from **making the feature work** to **making the feature reliable**.

I learned that software must be designed not only for normal situations, but also for unexpected situations.


## Completing the Save/Load Workflow

Previously, my project could successfully save and load game data.

```text
Game Object
        ↓
Dictionary
        ↓
JSON File
        ↓
Dictionary
        ↓
Game Object
```

However, I realized that this workflow only worked when everything was perfect.

I had not considered questions like:

- What if the save file does not exist?
- What if the JSON file is corrupted?
- Should the storage layer display error messages?
- Who should decide whether to create a new game?

These questions gradually became the main focus of today's work.


## Understanding File Management

Although I had already used `open()` before, today I gained a much deeper understanding of Python's file management.

I reviewed:

```python
open()
read()
write()
with open()
```

More importantly, I understood why `with open()` is recommended.

```python
with open(...) as file:
```

automatically closes the file even if an exception occurs.

This makes file operations much safer than calling `close()` manually.

I also realized that a file is simply another form of storage.

Program memory is temporary, while files allow data to persist after the program exits.


## Designing Exception Handling

The most important improvement today was adding exception handling to `load_game()`.

```python
try:
    with open(...) as file:
        data = json.load(file)
```

The project now handles two common situations.

### FileNotFoundError

When the save file does not exist,

the program does not crash.

Instead,

`load_game()` returns:

```python
None, "not_found"
```

and the program creates a brand-new game.


### JSONDecodeError

If the save file exists but its contents are damaged,

the program catches:

```python
json.JSONDecodeError
```

Instead of terminating unexpectedly,

the player receives a friendly message and a new game is created.

This makes the program much more robust.


## Separating Responsibilities

Another important lesson today was responsibility separation.

At first, I wanted `storage.py` to display error messages directly.

For example:

```python
show_save_not_found()
```

However, after discussing the architecture, I realized that this would make the storage layer depend on the UI layer.

Instead, the final design became:

```text
storage.py
        ↓
Returns (game, status)

main.py
        ↓
Coordinates program flow

ui.py
        ↓
Displays messages
```

`storage.py` only reports what happened.

It does not decide how the program should respond.

This keeps the dependency direction clean and allows each module to focus on its own responsibility.


## Returning Status Instead of Handling Everything

One design decision that impressed me today was changing:

```python
game = load_game()
```

into:

```python
game, status = load_game()
```

The storage layer no longer tries to solve every problem itself.

Instead, it reports the result to the application.

For example:

```python
"loaded"

"not_found"

"json_error"
```

The main program then decides what to do next.

This made me realize that a function's return value is also part of its interface design.


## Reflection

Today's lesson was not mainly about learning `try...except`.

Instead, it taught me how software should behave when something goes wrong.

I also gained a much deeper understanding of module responsibilities.

A storage layer should focus on file operations.

A UI layer should focus on displaying information.

The main program should coordinate the workflow.

I feel that I am gradually shifting my attention from writing Python syntax to designing software that is reliable, maintainable, and easier to extend.