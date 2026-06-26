# Installing and Configuring Git

## Step 1: Install Git

Official website:

[Git Official Website](https://git-scm.com/)

Download the version for your operating system.


## Recommended Installation Options

Most settings can remain default.

However, these options are important:

### 🟢 Editor

If you see:
>Choose the default editor used by Git

We recommend selecting your own IDE 

(e.g. PyCharm or VS Code)


Either one is fine.

If you don’t want to bother:
The default setting is fine.


### 🟢 PATH Option

If you see:
>Adjusting your PATH environment

We recommend selecting:

✅ Git from the command line and also from 3rd-party software.

This is the most universal option.

### 🟢 HTTPS Backend

Keep default settings.

### 🟢 Line Ending Conversion

Keep default settings.

### 🟢 Terminal Emulator

Default:

```text
MinTTY
```

is recommended.


## Verify Installation

Open Git Bash and run:

```bash
git --version
```

If you see:

```text
git version xxx
```

Git is installed successfully.


## Step 2: Configure Your Identity

Run these commands once:

```bash
git config --global user.name "YourGitHubName"
git config --global user.email "your@email.com"
```


## Step 3: Starting a Git Repository

Assuming your project is located at:
>D:\YourRepository

### Enter Project Directory

Example:

```bash
cd /d/YourRepository
```

How do I know if I’ve entered successfully?

Type: 

```bash
ls
```

If you see something like “main.py,”
it means you’ve entered successfully.

## Step 4: Initialize Git

Type:

```bash
git init
```

Meaning:

Git starts managing the project.


## Step 5: Add Files

Type:

```bash
git add .
```

Meaning:

Prepare all files for version tracking.


## Step 6: Create First Commit

Type:

```bash
git commit -m "first commit"
```

Meaning:

Save the first version

## Important Beginner Habit

In Git, Linux, and development environments, you often need to check “which directory you're currently in.”

Useful commands:

### 🟢 Show current directory

```bash
pwd
```

If you see:

```text
/d/YourRepository
```

It is already located in the project directory D:\YourRepository

### 🟢 List files

```bash
ls
```

If you can see "main.py" or "day1.py".

It means you’ve entered successfully.


### 🟢 Display Status

```bash
git status
```
If you see something like: 
>On branch master

or

>On branch main

this means Git is already managing the current project.


### In Git Bash:
`cd` means “change directory.”
For example: `cd /d/YourRepository`
Meaning: Enter this project directory.

### Before running commands like:

- `git add`
- `git commit`
- `python xxx.py`

always confirm your current directory.


### Otherwise beginners often:

- Run the wrong project
- Cannot find files
- Commit to the wrong repository

### A handy tip (you'll use this often)
Type: `ls`

Once you see: "main.py"

You can also run: `python main.py`

to run your Python program directly in the terminal.