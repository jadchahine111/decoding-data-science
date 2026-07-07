# Python Functions

> A **function** is a block of organized, reusable code that performs a single task. **Define once, use many times** (the *Don't Repeat Yourself* principle).

## Why We Need Functions

Without functions you'd have to repeat the same code everywhere. Functions give you **reusability**.

> 💡 **Example:** Calculating the area of a rectangle. Instead of copy-pasting the formula every time you need it, define it **once** as a function and reuse it.

---

## Defining a Function

Use `def`, followed by a descriptive name, then parentheses `()` holding the **parameters**, and end the line with a colon `:`.

```python
def greet(name):
    print("Hello " + name)
```

Defining it isn't enough — you have to **call** it:

```python
greet("Jad")        # Hello Jad
```

---

## Parameters vs. Arguments

| Term | What it is | Example |
|------|------------|---------|
| **Parameter** | The empty "slot" defined in the function recipe | `width`, `height` |
| **Argument** | The actual value poured into that slot when called | `10`, `5` |

```python
def rectangle_area(width, height):   # width, height → parameters
    print(width * height)

rectangle_area(10, 5)                # 10, 5 → arguments   →  prints 50
```

---

## Returning a Value

Use `return` to send an answer **back** from a function so you can store or reuse it.

```python
def add(a, b):
    return a + b

result = add(3, 4)
print(result)       # 7
```

> 💡 `print()` just *shows* a value on screen; `return` *hands it back* to your code so you can keep using it.

---

## Scope

**Scope** = where a variable can be seen or used.

- Variables created **inside** a function are **local** — they only exist there.
- They can't be accessed from **outside** the function.

```python
def my_function():
    x = 10          # x is local to this function
    print(x)

my_function()       # 10
print(x)            # ❌ NameError — x doesn't exist outside the function
```

---

## Example — Reusable Rectangle Area

```python
def rectangle_area(width, height):
    return width * height           # send the result back

# Define once, reuse many times:
room = rectangle_area(10, 5)
tile = rectangle_area(2, 3)

print(room)                         # 50
print(tile)                         # 6
print("Tiles needed:", room / tile) # Tiles needed: 8.333333333333334
```
