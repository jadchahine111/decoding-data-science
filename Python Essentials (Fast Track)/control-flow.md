# Python Control Flow

> **Control flow** = the order in which a program's statements are executed. It lets code be dynamic and responsive instead of running top-to-bottom every time.

## 1. `if` / `else` — Decision Making

- Runs different code depending on whether a condition is `True` or `False`.
- **Exactly one** of the branches runs — never both at once.

```python
if x > 0:
    print("x is positive")
else:                       # the opposite case (x <= 0)
    print("x is negative or equal to 0")
```

For multiple decisions, chain with `elif`:

```python
if x > 0:
    print("positive")
elif x == 0:
    print("zero")
else:
    print("negative")
```

> ⚠️ **Syntax reminders**
> - End every `if` / `elif` / `else` line with a colon `:` — forgetting it raises a `SyntaxError`.
> - Indent the code inside the block — wrong indentation raises an `IndentationError`.

---

## Repetition (Loops)

## 2. `while` Loop

- Keeps repeating **as long as** its condition stays `True`.
- Use it when you **don't know** in advance how many times to loop.

```python
n = 9
while n > 0:
    print(n)
    n = n - 1               # move toward ending the loop

# Output: 9 8 7 6 5 4 3 2 1
```

> ⚠️ **Infinite loop:** if you forget `n = n - 1`, the condition stays `True` forever and the loop never stops.

## 3. `for` Loop

- Repeats an action a **specific number of times**.
- Use `range(n)` to loop exactly `n` times.
- Use it when you **know** where the finish line is.

```python
for i in range(3):
    print("Action repeated")

# Output:
# Action repeated
# Action repeated
# Action repeated
```

> 💡 **Which loop?**
> - **`for`** → you know how many times to repeat.
> - **`while`** → you don't; you loop until a condition changes.

---

## Example — Find the Largest Number in a List

```python
numbers = [12, 5, 27, 8, 19]
largest_so_far = numbers[0]     # start by assuming the first item is largest

for num in numbers:
    if num > largest_so_far:    # found a bigger one?
        largest_so_far = num    # remember it

print(largest_so_far)           # 27
```
