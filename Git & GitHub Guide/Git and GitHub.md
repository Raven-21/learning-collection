# 1. Introduction to Git and GitHub

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


# 2. Installing and Configuring Git

## Step 1: Install Git

Official website:

[Git Official Website](https://git-scm.com?utm_source=chatgpt.com)

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


# 3. Connecting a Local Project to GitHub

## Step 1: Create a GitHub Repository

Go to:

[GitHub](https://github.com?utm_source=chatgpt.com)

Create a new repository.

Example repository name:

```text
YourRepository
```

Choose:

```text
Public
```


## Step 2: Connect Local Repository

GitHub will provide a command like:

```bash
git remote add origin https://github.com/USERNAME/YourRepository.git
```

Type it. This connects your local repository to GitHub.


## Step 3: Push Code

Type:

```bash
git push -u origin main
```

If you get:

```text
src refspec main does not match any
```

your branch may be named:

```text
master
```

instead of:

```text
main
```

Use:

```bash
git push -u origin master
```

instead.


## Check Remote Repository

Type:

```bash
git remote -v
```

This shows which GitHub repository is connected.


# 4. Updating GitHub Projects

Typical workflow:

```text
edit code → add → commit → push
```

## Step 1: Enter to the project directory

Open Git Bash:

Type:

```bash
cd /d/Code/YourRepository
```

## Step 2: Check Changes

Type:

```bash
git status
```
You will see something like: 

>modified: day1.py or: new file: guess_number.py


## Step 3: Add Changes

Type:

```bash
git add .
```
Meaning:

Prepare all files for version tracking.

## Step 4: Commit Changes

Type:

```bash
git commit -m "practice while loop"
```

What is a commit message? 

It’s simply a description of what was changed in this commit.

Recommendation:Keep it simple in English. 

For example: 

>add input practice, finish day 1 exercises, practice while loop

## Step 5: Push to GitHub

Type:

```bash
git push
```

Then refresh the GitHub page.

You will see:

- New code
- New commit

## Good Commit Habits

Do not wait too long before committing.

Recommended:

- Commit after completing small features
- Commit regularly

Examples:

```text
add input practice
finish guessing game logic
practice loops
```

Git is not only for saving code.

It also records your learning and development process.


# 5. Common Push Errors

Example error:

```text
fatal: unable to access
Recv failure: Connection was reset
```

Meaning:

The connection to GitHub was interrupted during upload.

This is usually a network problem rather than a code problem.


## Common Causes

- Unstable GitHub connection
- HTTPS push issues
- VPN or proxy problems
- Restricted school/company networks


## Possible Solutions

### Option 1: Retry

```bash
git push
```

Temporary network issues are common.


### Option 2: Check GitHub Website

Open:

[GitHub Website](https://github.com?utm_source=chatgpt.com)

If GitHub is slow or inaccessible, the issue is network-related.

### Option 3: Use GitHub SSH


This is a common approach among programmers.

Advantages:

- Less prone to disconnections
- No need for HTTPS authentication every time
- More stable

If you want a long-term solution (strongly recommended for future use)
- Generate an SSH key
- Add it to GitHub
- Update the remote URL


# 6. SSH Configuration for GitHub

SSH is a more stable authentication method than HTTPS.

SSH is generally:

- More stable
- Faster
- More convenient
- Better for long-term use


## Step 1 Generate SSH Key

Open Git Bash and type:

```bash
ssh-keygen -t ed25519 -C "your@email.com"
```

Next, you’ll be asked for:

**Save location**

Just press Enter (the default setting is fine):

Enter file in which to save the key

👉 Just press Enter

**Passphrase**

You can:
- Just press Enter (no passphrase—simple)
-  set a passphrase (more secure)

👉 Tip for beginners: Just press Enter twice

## Step 2: Show Public Key

Type:

```bash
cat ~/.ssh/id_ed25519.pub
```
It will output a long string:

>ssh-ed25519 AAAAC3... your@email.com


Copy the output.


## Step 3: Add SSH Key to GitHub

Go to:

GitHub → Settings → SSH and GPG keys → New SSH key

Fill in:
- Title: Enter anything (e.g., my laptop)
- Key: Paste the content you just copied

Then click:
>Add SSH key


## Step 4: Test SSH Connection

Open Git Bash and type:

```bash
ssh -T git@github.com
```

If successful, you will see:

```text
Hi USERNAME! You've successfully authenticated.
```

## Step 5: Change Remote URL to SSH

Enter to the project directory

```bash
cd /d/Code/YourRepository
```

Check current remote:

```bash
git remote -v
```

Before the change, you would see:

```text
https://github.com/xxx/xxx.git
```

Change HTTPS to SSH:

```bash
git remote set-url origin git@github.com:xxx/xxx.git
```

Verify SSH Remote

```bash
git remote -v
```

You should now see:

```text
git@github.com:xxx/xxx.git
```

## Note

When you connect to GitHub via SSH for the first time, Git shows a security prompt:

>The authenticity of host 'github.com' can’t be established. Are you sure you want to continue connecting?

This simply means your computer has never connected to GitHub before and is asking whether to trust the server.

It is a normal SSH security warning, not an error.

What you should do

Type:


```bash
yes
```

and press Enter.

What happens next
- Git saves GitHub’s fingerprint locally
- You won’t be asked again in the future
- The SSH connection process continues normally

Is this dangerous?

No.

This is a standard SSH security mechanism to prevent connecting to fake servers.

GitHub’s fingerprint is publicly known and trusted, so it is safe to accept.

When to be careful

Only be cautious if:

- You are not connecting to `github.com`
- The fingerprint does not match the official one

After successful connection

You should see a message like:

```
Hi username! You've successfully authenticated
```

At this point:

- SSH setup is complete
- GitHub connection is secure
- You can use `git push` normally without HTTPS authentication




## Step 6: Push Using SSH

```bash
git push
```

## HTTPS vs SSH

| Method | Authentication | Stability | Recommendation |
|---|---|---|---|
| HTTPS | Password / Token | Less stable | Basic |
| SSH | SSH Key | Very stable | Recommended |

## Final Recommendation

For long-term development:

✅ Use SSH  
✅ Commit regularly  
✅ Learn Git workflows early  
✅ Treat Git as part of programming itself