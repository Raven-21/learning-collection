# 🏗️ From Single Script to Multi-File Project: A Major Turning Point

One of the most important milestones in my Python learning journey was moving from a single-file program to a multi-file project structure.

This was the first time I experienced what it means to build a real software project instead of just writing scripts.


## 🔹 1. The Problem with a Single File

At first, everything was written in one file:

- input handling
- game logic
- data storage
- UI output
- control flow

As the project grew, the file became:

- harder to read
- harder to debug
- harder to extend

I realized:

> A single file cannot scale beyond a certain level of complexity.


## 🔹 2. Introducing Modular Thinking

To solve this, I started splitting the program into modules based on responsibility.

The project evolved into:

- main.py → controls the game flow
- data.py → manages game state and calculations
- logic.py → handles game rules
- ui.py → handles all output and display


This was my first experience with **modular programming**.


## 🔹 3. Understanding Imports and Dependencies

Splitting files introduced a new concept:

> Code is no longer globally accessible.

Now I had to explicitly connect modules:

```python
from data import create_game_state
from logic import check_guess
from ui import show_result
```

This helped me understand:

- how modules communicate
- how dependencies work
- why structure matters

## 🔹 4. Clear Separation of Responsibilities

Each file now had a clear purpose:

### data.py

Responsible for:

- game state creation
- statistics calculation
- derived values

### logic.py

Responsible for:

game rules
decision making

### ui.py

Responsible for:

- displaying information
- user-facing output

### main.py

Responsible for:

controlling program flow
coordinating modules

## 🔹 5. From Script to System

This change was more than just refactoring code.

It represented a mindset shift:

>From writing a script → to designing a system

I was no longer thinking about functions in isolation, but about how different parts of a program work together.

## 🧭 Summary

This was a turning point in my learning journey.

I learned that:

- structure matters more than size
- organization affects readability and scalability
- real programs are built from multiple cooperating modules

It was the first time my Python project started to resemble real-world software architecture.