# Python File Handling

> How to read from and write to files on disk.

## The 3 Steps of File Handling

1. **Open** the file
2. **Operate** on it (read / write)
3. **Close** the file

---

## 1. Manual File Handling

Open a file with the `open()` function:

```python
f = open('data.txt', 'r')   # opened in read mode
```

- **First argument** → the file path.
- **Second argument** → the mode:

| Mode | Meaning | Notes |
|------|---------|-------|
| `'r'` | Read | Default — file must already exist |
| `'w'` | Write | ⚠️ **Destructive** — erases and rewrites the entire file |
| `'a'` | Append | Adds to the **end**, keeping existing content |

> ⚠️ Because `'w'` wipes the whole file, use `'a'` when you just want to add something at the end.

### Operations

```python
# Read the whole file
content = f.read()

# Write (file must be opened in 'w' mode) — replaces all content
f.write("hello")

# Append (file must be opened in 'a' mode) — adds to the end
f.write("the end")
```

> ⚠️ **There is no `.append()` method for files.** To append, open the file in append mode (`'a'`) and use `.write()`. Appending is a *mode*, not a separate method.

### Closing

```python
f.close()
```

Manually closing matters — otherwise buffered data might not be saved correctly.

---

## 2. Automatic File Handling — the `with` Statement *(recommended, modern way)*

The `with` statement **closes the file automatically**, even if an error happens — so you never need to call `.close()` yourself.

```python
with open('data.txt', 'r') as file:
    ...
# file is automatically closed here
```

### Reading a file

```python
with open('data.txt', 'r') as file:
    for line in file:
        print(line.strip())    # .strip() removes surrounding spaces & newlines
```

### Writing to a file

```python
numbers = [1, 2, 3, 4, 5]

with open('numbers.txt', 'w') as f:
    for num in numbers:
        f.write(str(num) + '\n')   # convert to string, add a newline
```

---

## Example — Write Then Read Back

```python
# 1. Write a shopping list to a file
items = ["apples", "bread", "coffee"]

with open('shopping.txt', 'w') as f:
    for item in items:
        f.write(item + '\n')

# 2. Read it back and print each line
with open('shopping.txt', 'r') as f:
    for line in f:
        print(line.strip())

# Output:
# apples
# bread
# coffee
```
