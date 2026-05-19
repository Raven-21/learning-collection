# Python while Loop

## 1. What is a Loop?

A loop allows a program to repeat a block of code multiple times.

In simple words:

> “Do something again and again until a condition is false.”


## 2. Basic Structure

```python
while condition:
    # repeated code
```


## 3. Simple while Loop

```python
i = 1

while i <= 5:
    print(i)
    i += 1
```

Output:
```
1
2
3
4
5
```


## 4. Infinite Loop

If the condition never becomes False:

```python
while True:
    print("Hello")
```

⚠️ This runs forever unless stopped manually.


## 5. break Statement

Used to exit a loop early.

```python
i = 1

while True:
    print(i)
    if i == 5:
        break
    i += 1
```


## 6. continue Statement

Skips the current iteration.

```python
i = 0

while i < 5:
    i += 1
    if i == 3:
        continue
    print(i)
```

Output:
```
1
2
4
5
```


## 7. while vs if

| if | while |
|----|------|
| runs once | repeats many times |
| decision | repetition |


## 8. Common Pattern: Counter Loop

```python
count = 0

while count < 3:
    print("Hello")
    count += 1
```


## 9. User Input Loop

```python
password = ""

while password != "1234":
    password = input("Enter password: ")

print("Access granted")
```


## 10. Real Example: Guessing Game Style

```python
number = 7
guess = 0

while guess != number:
    guess = int(input("Guess the number: "))

    if guess > number:
        print("Too high")
    elif guess < number:
        print("Too low")

print("Correct!")
```


## 11. Infinite Loop + break Pattern (Very Common)

```python
while True:
    command = input("Enter command: ")

    if command == "exit":
        break

    print("You typed:", command)
```


## 12. Common Mistakes

### 1. Forgetting to update variable

```python
i = 1

while i <= 5:
    print(i)
    # missing i += 1 → infinite loop ❌
```


### 2. Wrong condition logic

```python
while i > 5:  # condition never true
```


### 3. Forgetting break in while True

```python
while True:
    pass  # infinite loop ❌
```


## 13. Key Ideas

- while repeats code based on condition
- must update variables inside loop
- `break` stops loop
- `continue` skips current step
- `while True` is used for game loops and programs


## 14. Think Like a Program

```text
Check condition → Run code → Update state → Repeat
```

Loop = the “heartbeat” of many programs.


## 15. Real Usage in My Projects

I already use while loops in:

- Guess number game main loop
- Replay system
- Input validation
- Game restart logic

👉 Without loops, programs cannot “run continuously”.