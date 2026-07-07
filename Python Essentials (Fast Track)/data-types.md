# Python Data Types

## Variable Naming Conventions

- Use **snake_case** (lowercase words joined by underscores)
- No spaces or special characters
- Can't start with a number

> 💡 **Dynamic typing:** You don't need to declare a variable's type in Python — it figures it out for you automatically.

---

## What Can We Store in a Variable?

### 1. Numbers

| Type | Description | Examples |
|------|-------------|----------|
| **Integer** (`int`) | Whole numbers | `10`, `-5`, `0` |
| **Float** (`float`) | Decimal numbers | `3.14`, `10.0` |

#### Math Operators

| Operator | Name | Example | Result |
|----------|------|---------|--------|
| `+` `-` `*` | Add, subtract, multiply | `1 + 1`, `2 * 5` | `2`, `10` |
| `/` | Division — **always** returns a float | `8 / 5` | `1.6` |
| `//` | Floor division — keeps the integer part only | `8 // 5` | `1` |
| `%` | Modulo — the remainder | `8 % 5` | `3` |
| `**` | Exponentiation — raise to a power | `2 ** 3` | `8` |

> ⚠️ **Watch out for floating-point rounding.**
> Floats can be subject to rounding issues, while integers are always exact.
>
> ```python
> 0.1 + 0.2   # 0.30000000000000004
> ```

### 2. Strings (`str`)

- Define a string with single quotes `'...'` or double quotes `"..."` — it doesn't matter which.
- Every character has an **index**, starting from `0`.

  ```python
  'Python'
  #  P → index 0
  #  y → index 1
  #  t → index 2  ...
  ```

- Strings are **immutable** — you can't change a single letter inside an existing string.

### 3. Booleans (`bool`)

- Only two possible values: `True` or `False`.

#### Comparison Operators (return a Boolean)

| Operator | Meaning | Example | Result |
|----------|---------|---------|--------|
| `==` | Equal to | `5 == 5` | `True` |
| `!=` | Not equal to | `5 != 3` | `True` |
| `>`  | Greater than | `5 > 3` | `True` |
| `<=` | Less than or equal to | `5 <= 3` | `False` |

> 🔎 **Truthiness:** Almost everything counts as `True` (e.g. `5`, `"Hello"`).
> The main values considered `False` are:
> - `0`
> - Empty string `""`
> - `None`

---

## Summary — The Core Data Types

| Type | Python name | Example |
|------|-------------|---------|
| Integer | `int` | `42` |
| Float | `float` | `3.14` |
| String | `str` | `"hello"` |
| Boolean | `bool` | `True` |

---

## Examples

```python
# 1. Integer — whole number
age = 25
print(age * 2)          # 50

# 2. Float — decimal number
price = 3.14
print(price + 1)        # 4.140000000000001  (float rounding!)

# 3. String — text, immutable, indexed from 0
name = "Python"
print(name[0])          # P

# 4. Boolean — result of a comparison
is_adult = age >= 18
print(is_adult)         # True
```
