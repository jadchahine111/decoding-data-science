# Python Data Structures

> The **4 essential data structures** in Python.

## 1. Lists `[]`

- **Ordered** — every element has a fixed position (index starts at `0`).
- **Mutable** — you can add, remove, or update elements.

```python
grades = [88, 92, 75]
print(grades[0])        # 88  (index 0)

grades.append(99)       # add an element
print(grades)           # [88, 92, 75, 99]  → the list itself is modified
```

## 2. Tuples `()`

- **Ordered** — just like lists, indexed from `0`.
- **Immutable** — a tuple cannot be modified after it's created.

```python
grades = (10.0, 20.5)
print(grades[0])        # 10.0  (index 0)
```

> ⚠️ **Single-item tuple:** you must add a trailing comma, otherwise it's not a tuple.
>
> ```python
> ('one',)    # ✅ a tuple
> ('one')     # ❌ just a string in parentheses
> ```

**Why use an immutable structure?** → To **protect data from changes**.

> 💡 **List vs. Tuple**
> - Use a **List** for a collection that needs to be modified.
> - Use a **Tuple** for data that should not be changed after it's created.

## 3. Sets `{}`

- **Unordered** — no indexing; you can't ask for a specific position.
- **Unique** — duplicates are automatically dropped.

```python
fruits = {"apple", "banana", "cherry"}

# Adding a duplicate has no effect
fruits.add("apple")
print(fruits)           # {"apple", "banana", "cherry"}
```

**Why use a set?** → Extremely **fast for membership tests** (checking whether an item exists).

## 4. Dictionaries `{key: value}`

- Store data as **key–value pairs**.
- Keys are **unique**.

```python
# A single dictionary
user = {
    "name": "Alice",
    "age": 30,
    "city": "New York"
}
print(user["name"])     # Alice

# A list of dictionaries
users = [
    {"name": "Alice",   "city": "New York", "age": 25},
    {"name": "Bob",     "city": "London",   "age": 30},
    {"name": "Charlie", "city": "Tokyo",    "age": 22}
]
```

**Why use a dictionary?** → When you have a clearly defined structure with a unique id, or when **labels matter more than order**.

---

## Summary

| Structure | Ordered? | Mutable? | Duplicates? | Use Case |
|-----------|----------|----------|-------------|----------|
| **List** `[]` | Yes | Yes | Yes | A collection you need to modify |
| **Tuple** `()` | Yes | No | Yes | A collection you want to protect |
| **Set** `{}` | No | Yes | No | Unique items & fast membership tests |
| **Dictionary** `{k: v}` | By key | Yes | Keys are unique | Mapping labels to data (key–value) |

---

## Example

```python
# A student record using all four structures together

subjects = ["Math", "Science", "History"]      # List   → ordered, editable
exam_dates = ("2026-06-01", "2026-06-08")       # Tuple  → fixed, protected
unique_grades = {88, 92, 88, 75}                # Set    → duplicates dropped → {88, 92, 75}

student = {                                     # Dictionary → labelled data
    "name": "Alice",
    "subjects": subjects,
    "grades": unique_grades,
    "exam_dates": exam_dates
}

print(student["name"])          # Alice
print(student["subjects"][0])   # Math
print(len(unique_grades))       # 3  (the duplicate 88 was removed)
```
