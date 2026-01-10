# 🤔 Open Questions

Questions I'm exploring as I learn. I'll update answers as I figure things out.

---

## Python Fundamentals

### ✅ How to iterate over multiple lists simultaneously without using index variables?
**Answered:** Use `zip()` function!
```python
l1 = [1, 2, 3]
l2 = ['a', 'b', 'c']
l3 = [10, 20, 30]

for x, y, z in zip(l1, l2, l3):
    print(x, y, z)
```
Also learned: `map(lambda x,y,z: x+y+z, l1, l2, l3)` achieves similar parallel processing.

---

### ✅ Why are dictionary lookups so much faster than list searches?
**Answered:** Hash tables! Dictionaries use hash functions for O(1) average lookup time. Lists need O(n) linear search.

When you access `dict[key]`, Python computes `hash(key)` and jumps directly to that memory location. For lists, Python has to check each element sequentially until it finds a match.

**Key takeaway:** Use dictionaries for frequency counting and lookups, lists for ordered sequences.

---

### 🔄 When to use OOP vs functional programming in data science?
**Still exploring...**

Initial thoughts:
- OOP: Building custom transformers, reusable pipelines, ML model classes
- Functional: Data cleaning, transformations (map/filter/reduce), quick analyses

Will revisit this after completing the OOP section.

---

## Object-Oriented Programming

### 🔄 What is the 'Diamond Problem' in multiple inheritance?
**Status:** Not covered yet. Will answer after inheritance module.

---

### 🔄 When should I use composition over inheritance?
**Status:** Waiting to complete Advanced OOP section.

---

## Data Analysis 

### 🔄 Why is NumPy faster than Python lists?
**Status:** Haven't started NumPy yet.

Hypothesis: Probably has to do with contiguous memory allocation and vectorized operations in C.

---

### 🔄 What's the difference between shallow copy and deep copy? When does it matter?
**Status:** Will explore in data structures module.

---

## Control Flow & Algorithms

### ✅ Why check only up to √n for prime numbers?
**Answered:** If `n = a × b`, one of them must be ≤ √n. So if no factor exists up to √n, none exists at all.

Example: For n=36, factors are (1,36), (2,18), (3,12), (4,9), (6,6). Notice 6 = √36 is the pivot—after that, pairs just flip. Checking up to 6 is enough.

**Complexity:** Reduces from O(n) to O(√n). For n=1,000,000, that's 1000 checks instead of 1,000,000.

---

### ✅ How to extract digits from a number without converting to string?
**Answered:** Use modulo and integer division:
```python
while num > 0:
    last_digit = num % 10    # remainder gives last digit
    num = num // 10          # integer division removes it
```
This is faster than `str(num)` and more "algorithmic." Used in: reversing numbers, Armstrong check, digit sum problems.

---

### 🔄 When to use `while` vs `for` loops?
**Current understanding:**
- `for`: When you know the number of iterations (iterating over collections, ranges)
- `while`: When termination depends on a condition (user input until 'quit', convergence in algorithms)

Still exploring: Are there performance differences? Does it matter for data science workflows?

---

### ✅ How do nested loops relate to pattern problems?
**Answered:** Think of them as coordinate systems! Outer loop = y-axis (rows), inner loop = x-axis (columns within that row).

The key insight: the inner loop's behavior usually depends on the outer loop's variable. For a triangle:
- Row 1: print 1 number
- Row 2: print 2 numbers
- Row n: print n numbers

So inner loop runs `i` times when outer loop is at iteration `i`:
```python
for i in range(1, n+1):        # which row
    for j in range(1, i+1):    # how many items in this row
        print(j, end=' ')
    print()
```

---

### 🔄 When should I use standard library functions vs writing my own implementation?
**Current thinking:**
- Learning: Write your own first to understand the algorithm
- Production: Use battle-tested library functions (they're optimized)
- Interviews: Know both approaches, ask which they prefer

Example: I wrote nested loops for permutations, then discovered `itertools.permutations` does it in one line. The exercise of writing it myself helped me understand it, but I'll use the library version in practice.

---

### 🔄 How do real-world applications handle floating point precision errors?
**Context:** In the clock angle problem, calculations like `30.5 * 7` can produce `213.50000000000003`.

**Status:** Need to research. Using `round()` for now, but there must be better practices.

---

## Data Structures

### ✅ When to use tuple vs list?
**Answered:**
- **Tuple:** Immutable, use for fixed records (coordinates, RGB values, database rows). Hashable so can be dict keys.
- **List:** Mutable, use when you need to modify elements, append, remove.

Tuples are also slightly faster for iteration and use less memory. If you're not modifying it, prefer tuple.

---

### ✅ `setdefault()` vs checking if key exists?
**Answered:** `setdefault()` is cleaner and atomic:
```python
# Instead of:
if key not in d:
    d[key] = []
d[key].append(value)

# Use:
d.setdefault(key, []).append(value)
```
One operation instead of two, and you avoid race conditions in concurrent code.

---

### 🔄 How do sets handle hash collisions?
**Context:** Sets use hashing for O(1) lookup, but what happens when two objects have the same hash?

**Status:** Need to research Python's collision resolution strategy. Related to why custom objects need both `__hash__` and `__eq__`.

---

### 🔄 Why can't lists be dictionary keys but tuples can?
**Current understanding:** Dict keys must be hashable. Lists are mutable, so their hash could change after being added as a key, breaking the dictionary.

Tuples are immutable, so their hash is stable. But what about tuples containing lists? Need to explore edge cases.

---

## Object-Oriented Programming

### ✅ What does `__` (double underscore) actually do in Python?
**Answered:** It's name mangling, not true privacy. `self.__var` becomes `self._ClassName__var`:
```python
class Foo:
    def __init__(self):
        self.__secret = 42

obj = Foo()
# obj.__secret  # AttributeError
obj._Foo__secret  # Works! Returns 42
```
Python's philosophy: "We're all consenting adults." It discourages access, doesn't prevent it.

---

### 🔄 When to use `@property` vs regular methods?
**Current thinking:**
- `@property`: When access looks like an attribute but needs computation (e.g., `circle.area`)
- Method: When it's clearly an action or takes parameters (e.g., `account.withdraw(100)`)

Still exploring: Are there performance implications?

---

### 🔄 What's the difference between `__str__` and `__repr__`?
**Current understanding:**
- `__str__`: Human-readable, for end users (what `print()` uses)
- `__repr__`: Unambiguous, for developers (what the REPL shows)

Rule of thumb: `__repr__` should ideally return something you could paste into Python to recreate the object.

---

*Questions will be added and answered as I progress through my learning journey.*
