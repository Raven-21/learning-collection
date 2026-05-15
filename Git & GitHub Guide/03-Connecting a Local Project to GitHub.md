# Connecting a Local Project to GitHub

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