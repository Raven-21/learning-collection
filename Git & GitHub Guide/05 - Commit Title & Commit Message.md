# Commit Title & Commit Message

A commit usually contains two parts:

```text
Commit Title

Commit Message (Description)
```

## Commit Title

The first line is a short summary of the changes.

Good examples:

```text
Add JSON persistence

Refactor game architecture

Improve Python notes

Release Guess the Number v1.0
```

Keep the title:

- short
- clear
- action-oriented

Usually less than 50 characters is recommended.


## Commit Message

The description explains what was changed and why.

Example:

```text
Improve Python notes and learning documentation

Updates include:
- Expanded File Processing notes
- Improved JSON documentation
- Added multiple exception handling examples
- Updated Python Learning Log
```

A good commit message helps both yourself and others understand the purpose of the commit in the future.


## Command Line

For a simple commit:

```bash
git commit -m "Improve Python notes"
```

For a detailed commit message:

```bash
git commit
```

Git will open the default editor.

Example:

```text
Improve Python notes

- Expanded File Processing notes
- Improved JSON documentation
- Updated learning logs
```

The first line is the **Commit Title**.

The remaining lines form the **Commit Message**.


## Common Commit Types

Different commits usually have different purposes.

| Type | Example |
|------|---------|
| Add | Add JSON persistence |
| Improve | Improve Python notes |
| Refactor | Refactor game architecture |
| Fix | Fix save/load bug |
| Release | Release Guess the Number v1.0 |
| Update | Update README |

Using consistent commit titles makes Git history much easier to read.


## Saving and Exiting the Commit Editor

When running:

```bash
git commit
```

Git may open the default text editor (often **Vim**) instead of committing immediately.

After writing the commit title and commit message:

1. Press **Esc** to leave Insert Mode.
2. Type:

```text
:wq
```

3. Press **Enter**.

Meaning:

```text
:w
```

Save the file.

```text
:q
```

Quit the editor.

Combined:

```text
:wq
```

Save and quit.

Git will then create the commit.


If you decide not to create the commit, press **Esc** and type:

```text
:q!
```

Then press **Enter**.

This exits without saving, and the commit will be cancelled.


## Tips

There are two common ways to create a commit.

### Simple Commit

```bash
git commit -m "Add JSON persistence"
```

No editor will open.


### Detailed Commit

```bash
git commit
```

Git opens the default editor, allowing you to write:

- Commit Title
- Commit Message

This is recommended for important commits such as project releases or major refactoring.


> **Note**

Many Git installations use **Vim** as the default commit editor.

Learning a few basic Vim commands (`Esc`, `:wq`, `:q!`) is enough for everyday Git usage.