# GitHub Releases

## What is a GitHub Release?

A GitHub Release is a published version of a project.

Unlike a normal commit, a release represents an important milestone, such as:

- v1.0
- v1.1
- v2.0

Releases make it easier for users to download stable versions of a project and understand what has changed.



## Git Commit vs GitHub Release

These two concepts are different.

### Git Commit

A commit records changes to the project.

Example:

```text
Add JSON persistence

Improve Python notes

Fix save/load bug
```

Commits happen frequently during development.


### GitHub Release

A release marks a stable version of the project.

Example:

```text
v1.0

First stable release
```

A release usually happens after multiple commits have been completed.



## Typical Workflow

A common workflow looks like this:

```text
Edit Code
      ↓
git add
      ↓
git commit
      ↓
git push
      ↓
Create Git Tag
      ↓
Publish GitHub Release
```

A release is usually the final step after finishing a feature or completing a project.



## Creating a Git Tag

Before creating a release, it is common to create a Git tag.

Example:

```bash
git tag -a v1.0 -m "First stable release"
```

Explanation:

- `v1.0` → Tag name
- `"First stable release"` → Tag message

After creating the tag:

```bash
git push origin v1.0
```

The tag is then uploaded to GitHub.



## Publishing a Release

After pushing the tag:

1. Open the GitHub repository.
2. Go to **Releases**.
3. Click **Create release from tag**.
4. Select the tag (for example `v1.0`).
5. Enter a release title.
6. Write release notes.
7. Click **Publish release**.

The project now has an official release.



## Release Title

A release title usually contains the project name and version.

Examples:

```text
Guess the Number v1.0

Expense Tracker v1.0

Todo CLI v2.0
```



## Release Notes

Release notes describe what changed in this version.

Example:

```text
Highlights

- Object-Oriented Programming
- JSON Persistence
- Exception Handling
- Project Documentation
```

Good release notes help users quickly understand the new version.



## Assets

GitHub automatically provides:

- Source code (zip)
- Source code (tar.gz)

Developers can also upload additional files, such as:

- Windows executable (.exe)
- macOS application
- Linux package
- PDF documentation

For small Python projects, the automatically generated source code is usually enough.



## Version Numbering

Common version numbers:

| Version | Meaning |
|---------|---------|
| v0.1 | Early prototype |
| v0.5 | Development version |
| v1.0 | First stable release |
| v1.1 | Small improvements |
| v2.0 | Major update |

There are many versioning strategies, but using clear version numbers makes project history easier to understand.



## Why Use Releases?

Releases provide several benefits:

- Mark stable versions.
- Keep project history organized.
- Make it easy to download older versions.
- Record important milestones.
- Improve project professionalism.

Releases are commonly used in open-source software projects.



## Best Practices

- Create releases only for meaningful milestones.
- Write clear release titles.
- Summarize major changes in the release notes.
- Keep version numbers consistent.
- Tag the project before publishing a release.



## Summary

A GitHub Release represents a stable version of a project.

Typical workflow:

```text
Develop
      ↓
Commit
      ↓
Push
      ↓
Tag
      ↓
Release
```

While commits record the development process, releases mark important milestones in a project's lifecycle.