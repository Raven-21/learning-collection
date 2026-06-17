# From `game_state` to `Game` Object

## Introduction

Today I officially started learning Object-Oriented Programming (OOP) through my Guess the Number project.

Instead of learning OOP from simple examples like `Dog` or `Student`, I decided to transform my existing modular project into an object-oriented design. This made the transition much more natural because I already understood the responsibilities and architecture of the project.


## Looking Back at the Modular Version

In the modular version, the entire game was built around a central state dictionary:

```python
game_state = {
    "number": random.randint(1, 100),
    "max_chance": max_chance,
    "history": []
}
```

Many functions depended on this dictionary:

```python
add_history(game_state, guess, result)

get_stats(game_state)

get_remaining_chance(game_state)

is_first_try(game_state)

check_guess(guess, game_state)
```

At first, this design worked well.

However, after studying the architecture more carefully, I noticed that almost every function was operating on the same piece of data: `game_state`.


## A Key Question

The most important question I asked myself was:

> If all these functions are working on the same state, why are they separated from the state itself?

This question led me directly to the motivation behind OOP.

Instead of storing data in a dictionary and passing it to multiple functions, I could combine the data and behaviors into a single object.


## Understanding Attributes and Methods

One of the biggest lessons today was learning the difference between attributes and methods.

### Attributes

Attributes describe what an object **is**.

For my game, these are:

```python
number
max_chance
history
```

These values belong to the game itself.


### Methods

Methods describe what an object **does**.

Examples include:

```python
add_history()

check_guess()

get_stats()

get_remaining_chance()
```

These behaviors operate on the game's state.


## Understanding `self`

At first, `self` looked mysterious.

After comparing it with my modular version, I realized that:

```python
game_state["history"]
```

became:

```python
self.history
```

And:

```python
game_state["number"]
```

became:

```python
self.number
```

The simplest way to understand `self` is:

> `self` means "this game object itself".

This made OOP much easier to understand.


## Building My First Game Class

I created my first `Game` class:

```python
class Game:

    def __init__(self, max_chance):
        self.number = random.randint(1, 100)
        self.max_chance = max_chance
        self.history = []
```

This replaced my old `create_game_state()` function.

Then I gradually migrated several functions into methods:

```python
add_history()

is_first_try()

get_remaining_chance()

check_guess()

get_stats()
```

For example:

```python
game.add_history(guess, result)
```

felt much more natural than:

```python
add_history(game_state, guess, result)
```

because the game now manages its own state.


## A New Way of Thinking

The biggest change today was not syntax.

The biggest change was perspective.

Previously, I thought:

```text
Functions operate on data.
```

Now I think:

```text
Objects own data and manage themselves.
```

This is the first time I truly understood why classes exist.

OOP is not just a new syntax feature.

It is a different way to organize a system.


## What I Learned Today

* Attributes represent an object's state.
* Methods represent an object's behavior.
* `self` refers to the current object.
* Data and the operations on that data should often stay together.
* OOP is not about creating classes everywhere.
* OOP helps organize complex systems more naturally.
* A `Game` object is a much better representation of my project than a large `game_state` dictionary.


## Next Steps

Next, I plan to migrate the core game flow into the `Game` class.

The goal is to transform:

```python
process_round(guess, game_state)
```

into:

```python
game.play_round(guess)
```

and continue building the OOP version of the project.

This will be the next major step in evolving my Guess the Number project from a modular design into a fully object-oriented design.
