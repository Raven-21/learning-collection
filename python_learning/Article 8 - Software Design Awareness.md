# 🧠 Software Design Awareness Begins to Emerge

During my Python learning journey, I gradually realized that writing code is not just about making things work. It is about designing how a program is structured and how different parts of the system interact with each other.

This was the stage where my thinking started to shift from “writing scripts” to “designing systems”.


## 🔹 1. From Code That Works → Code That Makes Sense

At first, my focus was simple:

- Make the program run
- Fix errors when they appear
- Add features step by step

However, as the project grew, I started to notice a problem:

> The code was working, but becoming harder to understand and manage.

This led me to rethink how I organize code.


## 🔹 2. Introduction of Layered Thinking

I started separating my program into different conceptual layers:

- Input Layer → handles user input
- Logic Layer → handles decision making
- Data Layer → manages game state
- Presentation Layer → handles output
- Control Layer → manages program flow

This was my first exposure to the idea of **layered architecture**.


## 🔹 3. State-Driven Thinking

Instead of using many independent variables like:

```python
number
history
stats
max_chance
```

I introduced a single unified structure:

```python
game_state = {
    "number": 42,
    "history": [],
    "max_chance": 10
}
```

This helped me understand:

>A program is easier to manage when state is centralized.

## 🔹 4. Separation of Concerns

Another important idea I started applying was:

>Each part of the program should have a single responsibility.

For example:

- Logic should not print messages
- UI should not decide game rules
- Data should not control flow

This made the code cleaner and easier to reason about.

## 🧭 Summary

This stage was not about learning new Python syntax.

It was about learning how to think about software:

- How to structure code
- How to organize responsibilities
- How to manage complexity

It marked the beginning of my transition from writing Python code to designing Python programs.