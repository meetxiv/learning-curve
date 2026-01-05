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

*Questions will be added and answered as I progress through my learning journey.*
