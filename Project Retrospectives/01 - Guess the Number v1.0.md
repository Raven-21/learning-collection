# Guess the Number v1.0

## Introduction

Today I officially completed and released **Guess the Number v1.0**, my first complete Python software project.

This project started as a very simple number guessing game and gradually evolved into a small object-oriented application through continuous learning, refactoring, and code reviews.

More importantly, this project was not only about building a game.

It became my first opportunity to experience the complete lifecycle of a software project, from planning and implementation to documentation and release.


## Project Timeline

The project evolved through multiple stages.

```text
Single Script
        ↓
Functions
        ↓
Modular Architecture
        ↓
State-Driven Design
        ↓
Object-Oriented Programming
        ↓
Storage Layer
        ↓
JSON Persistence
        ↓
Exception Handling
        ↓
Project Documentation
        ↓
GitHub Release v1.0
```

Looking back, each stage solved a different problem instead of simply adding more features.

The project gradually became easier to maintain, extend, and understand.



## Biggest Lessons

### Writing Working Code Is Only the Beginning

At the beginning of this project, my goal was simply to make the game work.

As the project grew, I gradually realized that software development involves much more than implementing features.

Questions such as:

- Which module should own this responsibility?
- Should this function belong to the Game class?
- Which data should be stored?
- Which values should be calculated?
- How should modules communicate?

became more important than simply making the program run.

This was my first experience thinking like a software engineer instead of only thinking about Python syntax.



### Refactoring Is Part of Development

One of the biggest surprises during this project was discovering that rewriting code is a normal part of software development.

Many functions were redesigned several times.

The project evolved from:

```text
One file
```

to

```text
Multiple modules
```

and finally to

```text
Object-Oriented Programming.
```

Each refactoring improved the structure without changing the game's functionality.

This taught me that good software is built through continuous improvement rather than writing perfect code on the first attempt.



### Software Design Is About Responsibilities

Throughout this project, I repeatedly discussed one question:

> "Where should this code belong?"

For example:

- Should saving data belong to the Game class or the Storage layer?
- Should error messages be displayed inside `storage.py`?
- Should derived data be stored or calculated?

These discussions helped me understand the importance of separation of concerns.

Instead of asking:

> "Can I put this code here?"

I gradually learned to ask:

> "Whose responsibility is this?"

This change in thinking was probably the most valuable lesson of the entire project.



## Technical Milestones

During this project, I learned and practiced:

### Python

- Functions
- Lists
- Dictionaries
- File I/O
- JSON
- Exception Handling

### Software Engineering

- Modular Architecture
- State-Driven Design
- Object-Oriented Programming
- Refactoring
- Separation of Concerns
- API Design

### Git & GitHub

- Git
- GitHub
- SSH Authentication
- Git Commit
- Git Push
- `.gitignore`
- Git Tag
- GitHub Releases

For the first time, I completed the entire workflow of developing and publishing a software project.



## Problems Discovered

Although the project reached version 1.0, I also found several possible improvements.

For example, the current save/load system restores the previous game state even after a game has already finished.

A better design would be introducing a **Save & Exit** feature that saves only unfinished games.

The loading function would then continue an unfinished game instead of replaying a completed one.

I intentionally decided not to implement this feature in version 1.0.

The purpose of this project is to build a solid foundation rather than continue adding new features indefinitely.

This decision also helped me understand an important software engineering principle:

> Every project needs a clear definition of "done."



## Reflection

When I started learning Python, I thought software development was mainly about learning syntax.

This project completely changed that idea.

Programming is not only about writing code.

It is also about organizing code, designing responsibilities, improving structure, and thinking about maintainability.

The Guess the Number project became much more than a small game.

It became my first complete software engineering practice.



## Looking Forward

Completing this project does not mean I have mastered Python.

Instead, it marks the end of my beginner stage.

The next project will allow me to focus less on basic syntax and more on solving practical problems with better software design.

My goal is to continue building increasingly complete projects and gradually develop the skills needed for real-world software development.



## Final Thoughts

This project represents the beginning of my journey from learning Python syntax to practicing software engineering.

Version **1.0** is not the end of this project.

It is the first milestone of a much longer journey.