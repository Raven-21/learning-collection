# Introduction to Git and GitHub

## What is Git?

Git is a version control system used to manage code history.

You can think of it as:

> A time machine and archive system for programmers.

## Why Do We Need Git?

When writing code, developers often need to:

- Fix broken code
- Restore older versions
- Track changes
- Collaborate with others
- Upload projects to GitHub

Git solves these problems.


### A Real Example

Suppose you wrote:

```python
print("hello")
```

Everything works correctly.

Then you continue editing the program and accidentally break it.

Without Git, many beginners create files like:

```text
final.py
final2.py
final_new.py
final_last.py
final_last_real.py
```

This quickly becomes messy.

With Git, you can save versions using commits:

```bash
git commit -m "finish login feature"
```

Even if the code breaks later, you can return to an older version easily.


# Git vs GitHub

Many beginners confuse these two concepts.


### Git is:

- A tool installed on your computer
- Responsible for version control
- Tracks file history and changes


### GitHub is:

- A cloud platform for hosting code
- A collaboration and portfolio website for developers

You can think of GitHub as:

> Cloud storage for code + a developer portfolio platform.


### Relationship Between Git and GitHub

```text
Git     = Local version manager
GitHub  = Remote cloud repository
```

## A Basic Workflow

Suppose you wrote:

```python
print("hello")
```

### Step 1: Add files

```bash
git add .
```

Meaning:

Prepare current changes for saving.


### Step 2: Create a commit

```bash
git commit -m "first version"
```

Meaning:

Save a version snapshot.


### Step 3: Upload to GitHub

```bash
git push
```

Meaning:

Upload local commits to GitHub.


## Why Git Is Essential

Real software development always involves:

- Code changes
- Version rollback
- Team collaboration
- Branch management
- Cloud synchronization

Git is considered a fundamental developer skill.