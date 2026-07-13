# 03 - Implementing Task Deletion

Today's work focused on implementing the task deletion feature while continuing to improve the overall architecture of the project.

Instead of concentrating only on writing code, I spent much more time thinking about software design, responsibilities, and the interaction between different modules.

## What I Implemented

Today I completed the deletion workflow of the project.

The workflow is now:

```text
Show Tasks
    ↓
User Selects a Task Number
    ↓
UI
    ↓
Main
(Convert task number to list index)
    ↓
TaskManager
    ↓
Validate Index
    ↓
Delete Task
    ↓
UI Displays Remaining Tasks
```

The project now supports:

* Displaying tasks with user-friendly numbering.
* Selecting a task by its number.
* Validating whether the selected task exists.
* Deleting the selected task.
* Displaying the updated task list after deletion.
* Handling invalid input through exception handling.

CRUD functionality has now reached another important milestone.


## What I Learned

### 1. Separating User Concepts from Internal Program Concepts

One of the most valuable lessons today was distinguishing between what users see and how the program stores data.

Users interact with task numbers:

```text
1
2
3
```

Internally, Python uses list indices:

```text
0
1
2
```

Instead of letting `TaskManager` perform this conversion, I decided to convert the user's task number into a list index inside `main.py`.

This keeps the manager independent from the user interface and allows it to focus only on managing data.


### 2. Keeping Responsibilities Consistent

I continued applying the same design principle used in previous components.

`TaskManager` is responsible for validating operations performed on its own data.

When an invalid index is provided, it raises a `ValueError` instead of silently ignoring the problem.

This keeps the design consistent with the validation strategy already used inside the `Task` class.


### 3. Building Features Before Optimizing Structure

Today's implementation also reminded me that software development often happens in stages.

At the moment, `main.py` is still acting as a temporary testing entry point.

Rather than building the final interactive menu immediately, the priority is to complete the core CRUD features first.

After the main functionality is finished, the program will be refactored into a proper menu-driven application using a continuous loop.


## Design Decisions

Current project decisions include:

* Users select tasks by task number.
* `main.py` converts task numbers into Python list indices.
* `TaskManager` validates indices before deleting tasks.
* Invalid operations raise exceptions instead of failing silently.
* The UI remains responsible for interacting with the user.

These decisions help keep responsibilities clear across different modules.


## Reflection

Compared with the previous project, I noticed that my attention is gradually shifting away from individual Python syntax.

Today, I spent much more time discussing why certain responsibilities belong to one module instead of another.

Questions such as where validation should happen, which layer should perform data conversion, and how different components communicate are becoming more important than simply writing code.

I also noticed that my own learning notes have started to become useful references during development. When deciding how to remove an element from a list, I reviewed my previous Python Notes before making the final design decision. This gave me confidence that maintaining a structured knowledge base is worthwhile.


## Next Step

The next stage of the project will continue expanding the CRUD functionality.

Planned work includes:

* Updating existing tasks.
* Finding tasks.
* Improving the interactive workflow.
* Building the final menu-driven application with a continuous program loop.