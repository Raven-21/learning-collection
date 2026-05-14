# 🧩 Refactoring Python Code: From a Simple Script to Structured Functions

> Once my Guess the Number game started working, I realized a new problem:  
> it worked, but the code was hard to read, hard to modify, and not well organized.

This is when I started learning about **code refactoring and functions**.

---

## 📌 Why I Started Refactoring

My first working version of the game was just one long `while` loop.

It worked, but it had problems:

- Too many repeated print statements
- Logic and display mixed together
- Hard to extend or debug
- Everything depended on one block of code

At this point, I learned an important idea:

> **Working code is not the same as good code.**

---

## 🧠 Key Idea: Functions Solve Structure Problems

I started breaking my code into smaller parts using functions.

Each function should do **only one thing**.

This idea changed how I think about programming.

---

## 🏗️ Before Refactoring (Bad Structure)

```python id="bef1"
while True:
    guess = int(input("Guess: "))

    if guess > number:
        print("Too high")
        print(f"You have {chance} chances left")
    elif guess < number:
        print("Too low")
        print(f"You have {chance} chances left")
    else:
        print("Correct!")
        break
```

### ❌ Problems:
- Repeated logic
- Hard to read
- Hard to reuse
- No separation of concerns

---

## 🔄 After Refactoring (Function-Based Structure)

I split the program into multiple functions:

---

### 🟢 Input Function

```python
def get_guess():
    try:
        return int(input("Guess the number: "))
    except ValueError:
        print("Invalid input!")
        return None
```

---

### 🟢 Logic Function
```python
def check_guess(current_guess, current_number):
    if current_guess > current_number:
        print("Too high")
        return False
    elif current_guess < current_number:
        print("Too low")
        return False
    else:
        print("Correct!")
        return True
```

---

### 🟢 Display Functions

```python
def show_count(count):
    print(f"You guessed {count} times")

def show_chance(chance):
    print(f"You have {chance} chances left")
```

---

## 🧠 What Changed After Refactoring

After splitting the code into functions:

**✔ Code became easier to read**

**✔ Each function had a clear responsibility**

**✔ Debugging became easier**

**✔ I could reuse logic more easily**

---

## ⚠️ Problems I Faced During Refactoring
### ❌ Problem 1: Too Many Functions

At first, I created too many small functions that didn’t add value.

### 💡 Insight:

Not everything needs to be a function — only meaningful logic should be separated.

---

### ❌ Problem 2: Confusion About Parameters

I struggled with passing variables like `guess`, `count`, and `chance`.

### 💡 Insight:

I learned that:

>Functions should receive data through parameters instead of relying on global variables.

Example:

```python
def check_guess(current_guess, current_number):
```

---

### ❌ Problem 3: Naming Confusion

I often reused variable names incorrectly or inconsistently.

### 💡 Insight:

Good naming improves readability more than I expected.

---

## 🧠 Biggest Concept I Learned

The most important idea from this stage was:

>Code should be organized for humans first, computers second.

Even if the program works, it is not “finished” if it is not readable.

---

## 🚀 What Refactoring Enabled

After refactoring, I could:

- Add features more easily
- Understand my own code after a break
- Fix bugs faster
- Extend the project into a more complete application

---

## 🎯 Final Structure After Refactoring

My project evolved into layers:

- Input Layer → `get_guess()`
- Logic Layer → `check_guess()`
- Display Layer → `show_count()`, `show_chance()`
- Game Loop → `while True`

---

## 🧭 Transition Point

This stage marked an important transition in my learning:

>From writing scripts → to designing structured programs

---

## 📌 Final Thoughts

Refactoring taught me that programming is not only about making something work.

It is also about:

- Clarity
- Structure
- Maintainability
- Thinking in systems

This was the first time I started thinking like a real developer.