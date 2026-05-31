# Python Learning Notes — State Management & Software Architecture

## Overview

During this stage of development, the project evolved from a function-based guessing game into a small state-driven application.

The focus shifted from learning Python syntax to learning how to organize code, manage data, and design software structures.


## 1. Dictionary (dict)

### Basic Structure

A dictionary stores data using key-value pairs.

Example:

```python
record = {
    "guess": 42,
    "result": "correct"
}
```


### Accessing Values

```python
record["guess"]
record["result"]
```


### Dictionary Traversal

Using `.items()`:

```python
for key, value in stats.items():
    print(key, value)
```

Used in the statistics system:

```python
for key, value in game_state["stats"].items():
    print(f"{key}: {value}")
```


## 2. Structured Data Design

Instead of storing guesses as simple numbers:

```python
history = [30, 50, 42]
```

The project evolved to structured records:

```python
history = [
    {"guess": 30, "result": "low"},
    {"guess": 50, "result": "high"},
    {"guess": 42, "result": "correct"}
]
```

Benefits:

* More information per record
* Easier data analysis
* Better scalability
* Clearer program state


## 3. Statistics System

Created a statistics dictionary:

```python
stats = {
    "high": 0,
    "low": 0,
    "correct": 0
}
```

Updating statistics dynamically:

```python
stats[result] += 1
```

This introduced:

* dynamic key access
* state tracking
* data aggregation


## 4. State-Driven Design

### Before

Game data was scattered across multiple variables:

```python
number
history
stats
max_chance
```


### After

Game data is centralized into a single state object:

```python
game_state = {
    "number": random.randint(1, 100),
    "max_chance": 10,
    "history": [],
    "stats": {}
}
```

Benefits:

* Centralized state management
* Easier data access
* Reduced parameter passing
* Better scalability


## 5. Data Layer

Introduced a dedicated Data Layer.

Responsibilities:

* Create application state
* Manage data structures
* Provide reusable data functions

Examples:

```python
create_game_state()
```

```python
get_remaining_chance()
```


## 6. State Management

The project now treats application data as a managed state.

Example:

```python
game_state["history"]
game_state["stats"]
game_state["number"]
```

Instead of managing many independent variables.

This is a foundational concept used in:

* Games
* Web applications
* Backend systems
* AI applications


## 7. Function Responsibility Design

Functions should have a clear responsibility.

Example:

### Logic Function

```python
check_guess()
```

Only determines:

```python
"high"
"low"
"correct"
```


### Presentation Function

```python
show_result()
```

Only displays information.


### Data Function

```python
get_remaining_chance()
```

Only calculates remaining attempts.


## 8. Parameter Reduction

Before:

```python
handle_round(
    guess,
    number,
    history,
    stats
)
```

After:

```python
handle_round(
    guess,
    game_state
)
```

Benefits:

* Cleaner function calls
* Easier maintenance
* Better scalability


## 9. Refactoring Mindset

Learned that software development is not only about making code work.

Code should also become:

* cleaner
* easier to understand
* easier to extend
* easier to maintain

Examples of refactoring:

* Removing duplicated logic
* Extracting functions
* Centralizing state
* Improving naming
* Reducing parameter complexity


## 10. Architectural Thinking

The project now follows a layered structure:

```text
Input Layer
↓
Logic Layer
↓
Data Layer
↓
Presentation Layer
↓
Game Layer
```

Key ideas:

* Separation of Concerns
* Layered Architecture
* State Management
* Data Flow Design


## Key Takeaway

This stage marked the transition from:

```text
Learning Python syntax
```

to:

```text
Learning software design
```

The focus is no longer just writing code that works, but understanding how to structure programs, manage state, and build maintainable systems.
