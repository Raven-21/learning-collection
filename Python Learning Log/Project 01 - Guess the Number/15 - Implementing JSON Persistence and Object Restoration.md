# Implementing JSON Persistence and Object Restoration

## Overview

Today I upgraded the persistence layer of my **Guess the Number** project.

Previously, the game only saved a human-readable text summary (`game_history.txt`).

Now the project stores structured game data in a JSON file and is able to restore a `Game` object from that file.

This is my first complete implementation of object serialization and deserialization.


## Why JSON?

Plain text is easy for humans to read, but difficult for programs to process.

For example, a text file like:

```text
Attempts: 5
Result: WIN
```

requires string parsing before the program can use the data.

JSON preserves the original data structure.

```json
{
    "number": 34,
    "max_chance": 10,
    "history": [
        {
            "guess": 50,
            "result": "high"
        }
    ]
}
```

After reading the JSON file, Python immediately converts it back into dictionaries and lists.


## Updating the Persistence Layer

I created two responsibilities inside `storage.py`.

### Saving

```text
Game Object
        ↓
Dictionary
        ↓
JSON File
```

`save_summary()` converts the `Game` object's state into a dictionary and writes it into `game_history.json`.


### Loading

```text
JSON File
        ↓
Dictionary
        ↓
Game Object
```

`load_game()` reads the JSON file, recreates the `Game` object, and returns it.

This allows the caller to work directly with a `Game` instance instead of dealing with file operations or dictionaries.


## Updating the Game Constructor

Originally, the constructor only supported creating a brand-new game.

```python
Game(max_chance)
```

After introducing JSON persistence, I modified the constructor to support restoring an existing game.

```python
Game(
    max_chance,
    number=None,
    history=None
)
```

If `number` or `history` is not provided, a new game is created.

Otherwise, the constructor restores the previous game state.

This makes one constructor support two different initialization scenarios.


## Design Decisions

### Raw State vs Derived State

Only raw state is stored in JSON.

Stored:

* number
* max_chance
* history

Not stored:

* remaining_chance
* is_first_try

Derived data can always be calculated from the raw state, so storing it would introduce unnecessary duplication.


### Returning Objects Instead of Dictionaries

`load_game()` returns a `Game` object instead of a dictionary.

```python
game = load_game()
```

This keeps file handling inside the storage layer and hides implementation details from the rest of the program.

This follows the idea of **Separation of Responsibilities**.


## Problems Discovered

Although the program can now successfully restore a game from JSON, I found a design problem.

Simply replacing

```python
game = Game(max_chance)
```

with

```python
game = load_game()
```

does not create a complete save/load system.

The program still needs proper game flow design, such as:

* starting a new game
* loading an existing game
* determining whether a saved game is still valid

This showed me that making the code work is different from designing a complete feature.


## Reflection

Today's work was not about learning a new Python syntax.

Instead, it was about connecting multiple concepts together.

```text
Game Object
        ↓
Dictionary
        ↓
JSON
        ↓
Dictionary
        ↓
Game Object
```

For the first time, I completed the entire data lifecycle inside one project.

This also helped me understand that software development is not only about writing functions, but also about designing how data flows through a program.