# Python break / continue

## 1. What are break and continue?

`break` and `continue` are control statements used inside loops.

They help you control the flow of repetition.


## 2. break (Stop the loop)

### Meaning:

> Exit the loop immediately.


### Example:

```python
for i in range(10):
    if i == 5:
        break
    print(i)
```

Output:
```
0
1
2
3
4
```


### How it works:

- Loop starts from 0
- When `i == 5`, loop stops completely


## 3. continue (Skip current step)

### Meaning:

> Skip the current iteration and go to the next one.


### Example:

```python
for i in range(5):
    if i == 2:
        continue
    print(i)
```

Output:
```
0
1
3
4
```


### How it works:

- When `i == 2`, skip printing
- Loop continues normally


## 4. break vs continue

| Keyword   | Effect                  |
|----------|------------------------|
| break    | stop the entire loop   |
| continue | skip current iteration  |


## 5. while loop with break

```python
while True:
    password = input("Enter password: ")

    if password == "1234":
        print("Access granted")
        break

    print("Wrong password")
```


## 6. while loop with continue

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


## 7. Real-world usage of break

### Stop game loop

```python
while True:
    command = input("Type 'exit' to quit: ")

    if command == "exit":
        break

    print("You typed:", command)
```


## 8. Real-world usage of continue

### Skip invalid input

```python
for i in range(5):
    if i == 0:
        continue  # skip 0

    print(10 / i)
```


## 9. Common mistakes

### 1️⃣ Using break incorrectly

```python
for i in range(5):
    break  # loop stops immediately
```


### 2️⃣ Forgetting loop logic after continue

```python
i = 0

while i < 5:
    if i == 2:
        continue  # ❌ infinite loop if i not updated
    i += 1
```


## 10. Key Ideas

- `break` → exit loop completely
- `continue` → skip current step
- both are used inside loops
- essential for controlling program flow


## 11. Think Like a Program

```text
Loop → check condition → decide:
    → stop (break)
    → skip (continue)
    → or continue normally
```


## 12. Real Usage in My Projects

I already use these in:

- Guess number game (break when correct)
- Input validation loops
- Replay system
- Menu-based programs

👉 These are core tools for building interactive programs.