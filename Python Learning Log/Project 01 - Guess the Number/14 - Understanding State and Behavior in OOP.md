# Understanding State and Behavior in OOP

## Introduction

Today I continued learning Object-Oriented Programming (OOP) through my Guess the Number project.

Instead of focusing on new syntax, I spent more time understanding how objects are designed and why OOP organizes code differently from procedural programming.

The most important thing I learned today was the relationship between **state** and **behavior**.


## From game_state to Game Object

Before learning OOP, my project used a centralized dictionary to store all game data.

```python
game_state = {
    "number": 42,
    "history": [],
    "max_chance": 10
}
```

Functions operated on this dictionary:

```python
check_guess(game_state, guess)
add_history(game_state, guess, result)
get_stats(game_state)
```

At that stage, I was already practicing state-driven design, but the data and the behaviors were still separated.

After refactoring the project into OOP, the structure became:

```python
game = Game(10)

game.check_guess(guess)
game.add_history(guess, result)
game.get_stats()
```

I realized that an object is not just a container for data.

An object combines both state and behavior.


## Understanding State

Inside my Game class:

```python
self.number
self.history
self.max_chance
```

These are all examples of state.

State describes the current condition of an object.

For example:

* `number` stores the target number.
* `history` stores previous guesses.
* `max_chance` stores the maximum number of attempts.

These values describe what the game currently is.


## Understanding Behavior

Methods represent behavior.

Examples:

```python
check_guess()
add_history()
play_round()
get_stats()
```

These methods perform actions or process data.

I started to see that OOP is not simply moving functions into a class.

The goal is to group related data and related behaviors together.


## Raw State vs Derived State

Another interesting concept I learned today is the difference between raw state and derived state.

Raw state is directly stored inside the object:

```python
self.number
self.history
self.max_chance
```

Derived state is calculated from other data.

For example:

```python
remaining_chance
```

can be calculated by:

```python
self.max_chance - len(self.history)
```

The object does not need to permanently store this value because it can always be derived from existing state.

This idea helped me understand why some values should be stored while others should be calculated when needed.


## Understanding **init**()

I also gained a clearer understanding of `__init__()`.

Previously, I thought `__init__()` was mainly responsible for creating objects.

Today I learned that its real purpose is to initialize object state.

Conceptually:

```text
Create Object
        ↓
Call __init__()
        ↓
Initialize State
```

The object is created first, and then `__init__()` prepares its initial data.


## Reflection

Today was less about learning new syntax and more about learning how to think in objects.

The biggest shift in my understanding was:

Before:

```text
Data + Functions
```

After:

```text
Object = State + Behavior
```

This idea connects naturally with the state-driven design concepts I learned earlier.

I feel that I am gradually moving from writing Python scripts to understanding software design.