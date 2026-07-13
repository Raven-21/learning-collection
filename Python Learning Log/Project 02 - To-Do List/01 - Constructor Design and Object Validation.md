# 01 - Constructor Design and Object Validation

Today I continued working on the second Python project, **To-Do List**. Although I wrote only a small amount of code, today's session focused much more on software design than programming syntax.

## What I Implemented

I completed the first version of the `Task` constructor.

Current design:

* `title` is required.
* `description` is optional and defaults to an empty string.
* `status` is automatically initialized to `"todo"`.

I also implemented validation to ensure that an object cannot be created with an empty title.


## What I Learned

### 1. Validate Before Assignment

One of the most important ideas I learned today is that validation should happen **before** assigning values to object attributes.

Instead of:

1. Assigning an invalid value.
2. Checking it afterward.

The better approach is:

1. Validate the input.
2. Raise an exception if necessary.
3. Assign the value only after it has passed validation.

This guarantees that every successfully created object starts in a valid state.


### 2. Fail Fast

Today I learned the **Fail Fast** principle.

If invalid data is detected, the program should stop object creation immediately by raising an exception instead of allowing an invalid object to exist.

Using:

```python
raise ValueError(...)
```

is not simply about handling errors—it is also a way to protect the integrity of the object.


### 3. Data Normalization

I learned that input data can be normalized before validation.

For the task title, I decided to remove leading and trailing whitespace using `strip()` before checking whether the title is empty.

This keeps stored data clean and avoids unnecessary formatting differences.


### 4. Required vs Optional Parameters

Today's discussion also changed the way I think about constructor parameters.

Instead of asking:

> "What attributes does this object have?"

I should first ask:

* Which attributes are required?
* Which ones are optional?
* Which values should be decided by the object itself?

This way of thinking makes constructor design much clearer.


## Design Decisions

After today's discussion, I decided that:

* `title` should be normalized using `strip()`.
* `description` will remain unchanged for now because it is free-form text, and preserving the user's original input is acceptable for the current version.

If future requirements change, this decision can be revisited during refactoring.


## Reflection

Today's progress reminded me that software development is not just about writing code.

Most of today's time was spent discussing *why* a design is better, rather than simply writing Python syntax.

Although the amount of code was small, I learned several important software engineering concepts:

* Object validation
* Constructor design
* Fail Fast
* Data normalization
* Object responsibility

Compared with my first project, I can clearly feel that I am beginning to think more about software design instead of only learning Python syntax.

This is exactly the direction I want to continue developing.

## Next Step

- Implement the TaskManager class.
- Continue learning object-oriented design.
- Improve project architecture step by step.