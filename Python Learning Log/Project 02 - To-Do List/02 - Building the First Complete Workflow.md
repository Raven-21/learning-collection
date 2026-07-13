# 02 - Building the First Complete Workflow

Today's development focused on connecting the individual components of the project into a complete workflow. Instead of creating isolated classes, I began thinking about how different objects should cooperate to accomplish a user task.

## What I Implemented

Today I completed the first end-to-end workflow of the project.

The current workflow is:

```text
User Input
    ↓
UI
    ↓
Main
    ↓
TaskManager
    ↓
Task
    ↓
Validation
    ↓
Store Task
    ↓
UI
    ↓
Display Tasks
```

The project can now:

* Create a task from user input.
* Validate the task title.
* Store the task in the manager.
* Display all existing tasks.
* Show an error message when invalid input is provided.

This is the first complete feature of the project.


## What I Learned

### 1. Designing Responsibilities Before Writing Code

Today reinforced an important idea:

> Design comes before implementation.

Instead of immediately writing methods, I first thought about the responsibilities of each class.

For example:

* `Task` represents a single task.
* `TaskManager` manages multiple tasks.
* `UI` communicates with the user.
* `main.py` coordinates the overall program flow.

Thinking about responsibilities first made the implementation much easier.


### 2. User Interface Includes Both Input and Output

Today I realized that a user interface is responsible for both directions of communication.

Input:

* Reading information from the user.

Output:

* Displaying information and error messages.

Previously, I tended to think that UI only meant printing text, but now I understand that `input()` is also part of the user interface.


### 3. Separating Program Flow from Business Logic

Another important lesson was separating responsibilities between modules.

`main.py` should not contain business logic.

Its responsibility is simply to organize the workflow:

1. Receive user input.
2. Call the appropriate manager.
3. Display the result.

This makes the program easier to understand and maintain.


### 4. Exception Handling Across Different Layers

Today I connected exception handling across multiple layers.

* `Task` detects invalid data.
* `Task` raises a `ValueError`.
* `main.py` catches the exception.
* `UI` displays a user-friendly error message.

This separation makes each component responsible for its own job.


## Design Decisions

Current project decisions include:

* `TaskManager` stores tasks using a list.
* `TaskManager` provides tasks through `get_tasks()`.
* `UI` handles both user input and output.
* `Task` is responsible for validating its own data.
* `main.py` coordinates the overall workflow without performing business logic.


## Reflection

Compared with my first project, I noticed a significant change in how I approach programming.

Previously, I focused mainly on Python syntax and writing individual functions.

Today, I spent much more time thinking about software design, object responsibilities, and how different components should work together.

Another important realization was that good code often comes from good design. Once the responsibilities of each class became clear, writing the actual code felt much more straightforward.

I also became more comfortable discussing design decisions instead of only asking how to write a specific line of code. This feels like an important step toward thinking like a software developer rather than simply learning Python syntax.


## Next Step

The next stage of the project will focus on expanding the capabilities of `TaskManager`.

Planned work includes:

* Deleting tasks.
* Finding tasks.
* Updating task information.
* Improving the interaction between the UI and the manager while keeping responsibilities clearly separated.