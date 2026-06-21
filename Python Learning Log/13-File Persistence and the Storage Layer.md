# File Persistence and the Storage Layer

## Introduction

Today I implemented the first file persistence feature in my Guess the Number project.

The goal was simple:

> Save game results to a file after each completed game.

Although the feature itself was not very large, it introduced several important software engineering concepts, including file I/O, persistence, and responsibility separation.


## The New Requirement

Previously, all game data existed only in memory.

For example:

```python
game.number

game.history
```

These values disappeared when the program stopped running.

I wanted to keep some information after the game ended, such as:

* The answer
* Number of attempts
* Game summary

To achieve this, I needed a way to save data outside the program.


## Understanding Persistence

One important concept I learned today is:

> Persistence means data can survive after the program exits.

Without persistence:

```text
Program Starts
    ↓
Game Runs
    ↓
Program Ends
    ↓
Data Disappears
```

With persistence:

```text
Program Starts
    ↓
Game Runs
    ↓
Save Data to File
    ↓
Program Ends
    ↓
Data Remains
```

This was my first practical experience with persistent storage.


## Learning File I/O

I used Python's file handling system:

```python
with open(
    "game_history.txt",
    "a",
    encoding="utf-8"
) as file:
```

Important concepts:

### open()

Used to open a file.

### "a" Mode

Append mode.

New content is added to the end of the file without deleting existing content.

### write()

Used to write text into the file.

### with Statement

Automatically closes the file after use.

This makes file handling safer and cleaner.


## Creating a Storage Layer

The most interesting design decision was where to place the saving logic.

My first thought was:

```python
class Game:

    def save_game(self):
        ...
```

Because saving seemed related to the game.

However, after thinking about responsibilities, I realized:

The game manages:

* Game state
* Game rules
* Round processing

But file operations are actually related to:

* Files
* Storage
* Persistence

These responsibilities are different.


## Introducing storage.py

Instead of placing file operations inside the Game class, I created a dedicated module:

```text
storage.py
```

This module is responsible for:

* Saving data
* Reading data (future)
* Managing persistence

The Game object only provides data.

The Storage layer decides how to save it.


## Responsibility Separation

The architecture became:

```text
Game
    ↓
Provides data

Storage
    ↓
Stores data

Main
    ↓
Coordinates workflow
```

For example:

```python
show_summary(game)

save_summary(game)
```

The Game object does not need to know anything about files.

This keeps responsibilities clean and focused.


## What I Learned

Today I learned:

* Basic file I/O in Python
* The difference between memory and persistent storage
* How append mode works
* Why file operations deserve their own layer
* How responsibility separation applies to real features
* How architecture decisions become more important as projects grow

Most importantly, I learned that:

> A feature is not only about making it work. It is also about deciding where it belongs.


## Project Evolution

```text
Single Script
    ↓
Functions
    ↓
Modular Architecture
    ↓
State-Driven Design
    ↓
Object-Oriented Design
    ↓
Storage Layer & Persistence
```

The project now keeps game data beyond program execution, marking my first step into persistent data management.


## Next Steps

Possible future improvements:

* Load saved game history
* Display previous game results
* Track total games played
* Calculate win rate
* Save data in JSON format
* Build a more complete persistence system

This is my first experience designing a storage layer, and it helped me understand how software projects continue growing beyond core functionality.