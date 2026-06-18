# Refactoring Guess the Number into OOP

## Introduction

Today I completed the first object-oriented version of my Guess the Number project.

Previously, the project was built around a centralized `game_state` dictionary and a collection of functions spread across multiple modules.

After learning the fundamentals of Object-Oriented Programming (OOP), I successfully refactored the project into a class-based design centered around a `Game` object.

This marks an important milestone in my transition from modular programming to object-oriented thinking.


## The Original Design

The modular version used a shared state dictionary:

```python
game_state = {
    "number": random.randint(1, 100),
    "max_chance": max_chance,
    "history": []
}
```

Many functions depended on this structure:

```python
check_guess()

add_history()

get_stats()

get_remaining_chance()

process_round()
```

The architecture worked well, but most functions were tightly connected to the same state object.


## Building the Game Class

The first step was creating a dedicated `Game` class.

```python
class Game:

    def __init__(self, max_chance):
        self.number = random.randint(1, 100)
        self.max_chance = max_chance
        self.history = []
```

The old `game_state` dictionary was replaced with object attributes.

Instead of:

```python
game_state["history"]
```

I now use:

```python
game.history
```

This made the code more natural and easier to understand.


## Migrating Functions into Methods

I gradually moved several functions into the `Game` class.

### State Management

```python
add_history()
```

### Derived Data

```python
get_stats()

get_remaining_chance()

is_first_try()
```

### Game Rules

```python
check_guess()
```

### Round Processing

```python
play_round()
```

This allowed the `Game` object to manage both its state and its behavior.


## The Most Important Refactor

The biggest architectural change was replacing:

```python
process_round(guess, game_state)
```

with:

```python
game.play_round(guess)
```

Instead of coordinating multiple functions externally, the `Game` object now handles the entire round internally.

The game is responsible for:

* Checking the guess
* Recording history
* Calculating remaining chances
* Determining win/lose status
* Returning round results

This significantly improved encapsulation.


## Separation of Responsibilities

After the refactor, the architecture became much cleaner.

### Game Class

Responsible for:

* Game state
* Game rules
* Round processing
* Statistics

### UI Module

Responsible for:

* Displaying messages
* Showing history
* Showing statistics
* Presenting results

### Main Module

Responsible for:

* Program flow
* User input
* Replay system

This separation makes the project easier to maintain and extend.


## Understanding Encapsulation

One concept became much clearer during this refactor:

> Data and the operations on that data should stay together.

Instead of writing:

```python
add_history(game_state, guess, result)
```

I now write:

```python
game.add_history(guess, result)
```

The object already owns its data, so there is no need to pass the state around constantly.

This made OOP feel much more practical than simply learning class syntax.


## Testing the New Version

After the migration, I tested:

* Normal win condition
* Lose condition
* First-try win
* Guess history tracking
* Statistics generation

All tests passed successfully.

The OOP version behaves exactly like the modular version while providing a cleaner internal design.


## What I Learned

Today I learned:

* How to transform a modular project into an object-oriented project
* How to identify which functions belong inside a class
* How encapsulation reduces dependency on shared state
* How a class can manage both data and behavior
* How OOP improves code organization without changing program functionality

Most importantly, I learned that OOP is not about creating classes for everything.

It is about finding the right object to represent a real system.


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
```

The Guess the Number project has now completed its first OOP refactor.


## Next Steps

Planned improvements:

* Further improve the Game class design
* Explore additional OOP concepts
* Add file persistence
* Improve project scalability
* Continue developing engineering-oriented programming skills