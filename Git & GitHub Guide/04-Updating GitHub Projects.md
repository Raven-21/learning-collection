# Updating GitHub Projects

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