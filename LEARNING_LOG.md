# 📖 Learning Log

A daily record of my learning journey—wins, struggles, and insights.

---

## January 2026

### Day 1 | Jan 3, 2026

**What I did:**  
Set up this repository and planned my learning path. Decided to document everything publicly.

**Why Data Science?**  
I've always been curious about how data drives decisions. Instead of just watching tutorials, I'm committing to building real understanding through practice.

**My approach:**  
- Start with strong Python fundamentals
- Don't rush to ML—understand the foundations first
- Document what I learn, including mistakes
- Build small projects as I go
- No matter how hard the problem is, be consistent, take breaks, google and build problem solving thinking. 

**Today's realization:**  
There's no shortcut. Everyone who's good at this put in the hours. My job is to show up consistently.

**Next:** Starting with Python basics—variables, data types, operators.

---

### Day 2 | Jan 4, 2026

**What I did:**  
Completed 10 Python exercises on variables, data types, and operators.

**Key insights:**

**1. `print()` is more powerful than you think:**  
The `sep` and `end` parameters make formatting cleaner than string concatenation:
```python
print(a, b, c, sep=' | ')     # separator between items
print("Loading", end='...')   # no newline at end
```
`sep` works within one `print()`, `end` controls what happens after.

**2. One-liner input conversion:**  
Converting comma-separated user input to numeric tuple:
```python
tuple(map(int, input().split(',')))  # "1,2,3" -> (1, 2, 3)
```
The `map()` + `split()` combo is everywhere in competitive programming.

**3. Validate before calculating:**  
In the dogs-chickens problem, I learned to check constraints first (legs must be even, within valid range) before attempting calculation. Fail early, fail clearly.

**4. Floor division for discrete quantities:**  
`//` vs `/` matters when counting whole items:
```python
milk_glasses = total_ml // 250  # can't have 2.5 glasses
```

**Struggled with:**  
Initially overcomplicated the chicken-dogs problem with rule-based constraints and factorization. Later realized it's just basic linear algebra: 2 equations, 2 unknowns.

**Realization:** THINKING ELEMENTARY SOLVES THE PROBLEM.

---

### Day 3 | Jan 5, 2026

**What I did:**  
Solved 15 miscellaneous Python problems covering lists, strings, dictionaries, and functional programming concepts (map, filter, reduce).

**Key insights:**

**1. `set()` for instant uniqueness:**  
Fastest way to get unique elements—O(1) average lookup:
```python
unique_items = list(set(my_list))
```

**2. `*args` unpacking power:**  
Used it to merge an arbitrary number of dictionaries:
```python
def merge_dicts(*dicts):
    result = {}
    for d in dicts:
        result.update(d)
    return result
```
`*args` is a tuple, `**kwargs` is a dictionary.

**3. `dict.get()` prevents KeyError:**  
Essential pattern for frequency counting:
```python
freq[word] = freq.get(word, 0) + 1  # no KeyError if word is new
```

**4. Histogram binning trick:**  
Integer division finds bin boundaries without if-else chains:
```python
bin_start = value // 10 * 10  # 47 -> 40, 83 -> 80
```

**5. Functional programming chains:**  
- `map()` processes multiple lists in parallel: `map(lambda x,y,z: x+y+z, l1, l2, l3)`
- `reduce()` flattens 2D lists elegantly: `reduce(lambda x,y: x+y, list_2d)`
- Chaining `filter()` and `map()` enables complex one-liners

**Struggled with:**  
The histogram problem—had to figure out dynamic bin generation based on data's min/max. Also, nested lambda functions took some trial and error.

---

### Day 4 | Jan 6, 2026

**What I did:**  
Solved 14 problems on conditionals and control flow—salary calculations, number theory (primes, Armstrong, Fibonacci), and a robot movement tracker.

**Key insights:**

**1. Prime number optimization:**  
Only check up to √n. If a number has a factor greater than its square root, it must also have one smaller:
```python
for num in range(2, int(n**0.5) + 1):  # O(√n) not O(n)
```

**2. Digit extraction without strings:**  
Process each digit mathematically:
```python
while num > 0:
    digit = num % 10   # extract last digit
    num //= 10         # remove last digit
```
Used for reversing numbers, Armstrong check. Pure math > string manipulation.

**3. State machines with dictionaries:**  
Robot tracker using dict as state:
```python
moves = {'U': 0, 'D': 0, 'L': 0, 'R': 0}
moves[direction] += distance
```
Much cleaner than multiple if-else chains.

**4. Clock angle = rate problem:**  
Minute hand: 6° per minute (360°/60). Hour hand: 0.5° per minute (30°/60). Think in rates, not positions.

**5. Loop control flow:**  
`continue` (skip iteration) + `break` (exit loop) for complex conditions like "sum until 300, but skip multiples of 5."

**Struggled with:**  
Clock angle problem—I was calculating positions instead of relative movement. Had to think mathematically: both hands start at 12, angle is just the difference in their positions.

**Realization:**  
Most "tricky" problems become simple once you identify the underlying math. The code is just translating math to syntax.

---

### Day 5 | Jan 7, 2026

**What I did:**  
Worked on loop problems—pattern printing, series calculations, string manipulations. The classic nested loops territory.

**Key insights:**

**1. Nested loops are just 2D thinking:**  
Pattern problems clicked when I started visualizing them as coordinate systems. Outer loop = row (y), inner loop = column (x). For the descending triangle:
```python
for i in range(n, 0, -1):      # rows: 5,4,3,2,1
    for j in range(i, 0, -1):  # cols in each row
        print(j, end=' ')
    print()
```
The trick is figuring out how the inner loop's range relates to the outer loop's variable.

**2. Pyramid spacing formula:**  
For centered pyramids, spaces decrease as stars increase. If you're at row `i`, you need `n-i` leading spaces:
```python
print(' ' * (n - i), end='')
print('* ' * i)
```
Simple once you see it, but took me a while to derive instead of just copying.

**3. Building numbers mathematically (series trick):**  
For series like `2 + 22 + 222 + 2222...`, instead of string concatenation, use math:
```python
s = 0
for i in range(n):
    s = s * 10 + 2   # s becomes: 2, 22, 222, 2222...
    sum += s
```
Each iteration shifts left (multiply by 10) and adds the digit. This is how you build numbers programmatically.

**4. `itertools.permutations` is a lifesaver:**  
When asked to print all unique arrangements of [1,2,3,4], I initially thought about 4 nested loops. Then discovered:
```python
from itertools import permutations
for p in permutations([1,2,3,4]):
    print(*p)
```
Learning when to use the standard library vs reinventing the wheel is a skill itself.

**5. String symmetry without slicing tricks:**  
To check if a string like "khokho" is symmetrical (both halves same):
```python
first_half = s[:len(s)//2]
second_half = s[-(len(s)//2):]  # negative indexing from end
```
The `-n:` slice syntax is cleaner than calculating `len(s)//2` for the start index.

**6. Character classification loop:**  
For sorting characters by type (lowercase, uppercase, others), three accumulators work better than sorting:
```python
for char in s:
    if char.islower(): lowercase += char
    elif char.isupper(): uppercase += char
    else: other += char
```
One pass, O(n), no sorting overhead.

**Struggled with:**  
The pyramid pattern alignment. I kept getting off-by-one errors with the spaces. Had to actually draw it out on paper, number the positions, and trace through my loop manually before the formula clicked.

**Realization:**  
Pattern problems aren't really about patterns—they're about finding the mathematical relationship between row number and what gets printed. Once you find that formula, the code writes itself.

---

### Day 6 | Jan 8, 2026

**What I did:**  
Deep dive into Python's core data structures—tuples, sets, and dictionaries. Practiced problems that combine them in interesting ways.

**Key insights:**

**1. `setdefault()` is underrated:**  
For grouping data by a key, this is cleaner than checking if key exists:
```python
groups = {}
for key, value in data:
    groups.setdefault(key, []).append(value)
# No need for: if key not in groups: groups[key] = []
```
It returns the existing value OR sets and returns the default—all in one operation.

**2. Sets for membership testing:**  
When checking if elements exist across multiple collections, set intersection is O(n):
```python
common = set(ar1) & set(ar2) & set(ar3)  # elements in ALL three
```
Way faster than nested loops checking each element.

**3. Binary string = exactly 2 unique characters:**  
Elegant one-liner using set comprehension:
```python
is_binary = len(set(string)) == 2
```
I initially thought about checking for '0' and '1', but the actual definition is broader.

**4. `zip()` for parallel dictionary construction:**  
Converting list to list of dictionaries:
```python
# Verbose way with nested loops
# Elegant way:
result = [dict(zip(keys, values[i:i+len(keys)])) 
          for i in range(0, len(values), len(keys))]
```
`zip()` pairs up keys with corresponding values automatically.

**5. Sorting dictionaries properly:**  
`sorted(dict.items())` returns sorted tuples, but you need to reconstruct:
```python
sorted_dict = {k: sorted(v) for k, v in sorted(original.items())}
```
Sorts both keys AND the value lists.

**6. Type checking in mixed collections:**  
`type()` returns the actual class, useful for counting:
```python
counts = {}
for item in mixed_list:
    counts[type(item)] = counts.get(type(item), 0) + 1
# {<class 'list'>: 2, <class 'set'>: 2, <class 'tuple'>: 1}
```

**Struggled with:**  
The tuple grouping problem—joining `(5,6), (5,7), (5,8)` into `(5,6,7,8)`. Initially tried complex list manipulations. Then discovered `setdefault()` + unpacking makes it trivial. Sometimes the right tool makes the problem disappear.

**Realization:**  
Tuples, sets, and dicts aren't just "data containers"—they're problem-solving tools. Sets for uniqueness/membership, dicts for grouping/lookup, tuples for immutable records. Choosing the right structure is half the solution.

---

### Day 7 | Jan 9, 2026

**What I did:**  
List comprehensions day. Solved 15 problems focusing on condensing logic into single expressions—matrix operations, string transformations, running sums.

**Key insights:**

**1. `zip()` is the secret weapon:**  
For combining lists index-wise, forget manual indexing:
```python
[[x, y] for x, y in zip(list1, list2)]
# ["M", "na", "i"] + ["y", "me", "s"] -> [["M","y"], ["na","me"], ["i","s"]]
```
`zip()` handles unequal lengths gracefully by stopping at the shortest.

**2. Running sum with slicing:**  
Elegant but O(n²) approach using cumulative slices:
```python
[sum(list1[:i]) for i in range(1, len(list1)+1)]
# [1,2,3,4] -> [1, 3, 6, 10]
```
For production, use `itertools.accumulate()` for O(n).

**3. Nested list comprehension order matters:**  
For flattening matrices, the loop order in comprehension mirrors nested for-loops:
```python
# Nested loops:          # Comprehension:
for r in range(3):       [matrix[r][c] for r in range(3) for c in range(3)]
    for c in range(3):
        matrix[r][c]
```
First `for` is outer, second `for` is inner. Same order.

**4. Matrix transpose in one line:**  
Swap row and column indices:
```python
transpose = [[matrix[r][c] for r in range(3)] for c in range(3)]
```
Outer loop iterates columns, inner loop iterates rows—that's the swap.

**5. String join + split for list flattening:**  
Quick way to flatten list of strings:
```python
' '.join(list_of_strings).split()
# ['hello world', 'foo bar'] -> ['hello', 'world', 'foo', 'bar']
```
Join with space, then split on whitespace. Simple but clever.

**6. Custom sorting with `zip()` trick:**  
To sort by computed values without losing original data:
```python
scores = [compute_score(item) for item in items]
sorted_items = [x[-1] for x in sorted(zip(scores, items), reverse=True)]
```
Zip scores with items, sort by scores, extract items.

**Struggled with:**  
The alphanumeric sorting problem—sort strings by product of their digits. Had to think about it in steps: extract digits → compute product → pair with original → sort → extract. Breaking complex transformations into pipeline steps helps.

**Realization:**  
List comprehensions aren't just "shorter loops"—they're a way to think about data transformations as pipelines. Input → Transform → Output. Once you see it that way, complex operations become compositions of simple ones.

---

### Day 8 | Jan 10, 2026

**What I did:**  
Started Object-Oriented Programming. Built classes for Rectangle, BankAccount, and a FlashCard quiz game. Focus on encapsulation—hiding data, exposing behavior.

**Key insights:**

**1. Double underscore = name mangling (not true private):**  
Python's `__variable` isn't actually private—it just mangles the name:
```python
class Bank:
    def __init__(self):
        self.__balance = 1000  # becomes _Bank__balance

obj = Bank()
print(obj._Bank__balance)  # Still accessible, just discouraged
```
It's a convention, not enforcement. Python trusts developers.

**2. `__str__` for human-readable representation:**  
Define how your object looks when printed:
```python
def __str__(self):
    return f'Rectangle({self.__length}, {self.__width})'
# Now print(obj) shows: Rectangle(4, 5)
```
Without it, you get `<__main__.Rectangle object at 0x...>`. Useless.

**3. Methods that use other methods:**  
`display()` calling `perimeter()` and `area()` internally:
```python
def display(self):
    print(f'Perimeter = {self.perimeter()}')  # self.method()
    print(f'Area = {self.area()}')
```
Build complex behavior from simple methods. Composition over duplication.

**4. Business logic in methods, not outside:**  
Bank withdrawal with fee calculation inside the class:
```python
def withdraw(self, amount):
    if amount > self.__balance:
        print('Insufficient funds!')
    else:
        self.__balance -= self.bankFees(amount)
```
The class knows its rules. Caller doesn't need to know about fees.

**5. `random.choice()` on dict items:**  
For the FlashCard quiz, picking random key-value pairs:
```python
fruit, color = random.choice(list(self.__fruitlist.items()))
```
`dict.items()` returns view, need `list()` for `random.choice()`.

**6. Game loops with class state:**  
The FlashCard class maintains its own data, the `quiz()` method handles the loop:
```python
while True:
    # ask question using self.__data
    if user_wants_to_exit:
        break
```
State (questions) is encapsulated, behavior (quiz logic) is exposed.

**Struggled with:**  
Initially put the bank fee calculation outside the class. Then realized—if the fee percentage changes, every place that calls `withdraw()` would need updating. Encapsulating it means one change, one place.

**Realization:**  
OOP isn't about making things complicated—it's about organizing code so that related data and behavior live together. The BankAccount class "knows" how to handle deposits, withdrawals, and fees. Users of the class don't need to know the implementation details.

---

### Day 9 | Jan 11, 2026

**What I did:**  
Inheritance in OOP. Built a Bus class extending Vehicle, learned how child classes override parent methods while still using parent functionality.

**Key insights:**

**1. `super().__init__()` calls parent constructor:**  
```python
class Bus(Vehicle):
    def __init__(self, capacity=50):
        super().__init__(capacity)  # Parent sets up base attributes
```
Without `super()`, parent's `__init__` never runs—attributes won't exist.

**2. Override method but still access parent's version:**  
Bus has its own `fare()` but needs the base calculation:
```python
def fare(self):
    base_fare = self.get_seating_capacity() * 100
    return base_fare * 1.1  # Add 10% maintenance
```
Use getter methods when parent attributes are private (`__`).

**3. Default arguments in child classes:**  
Child can have different defaults than parent:
```python
class Vehicle:
    def __init__(self, capacity):  # Required
        
class Bus(Vehicle):
    def __init__(self, capacity=50):  # Optional with default
```

**Struggled with:**  
Accessing `self.__seating_capacity` from child class—got AttributeError. Private attributes aren't inherited directly. Had to use parent's getter method instead.

**Realization:**  
Inheritance is about extending, not copying. The child says "I'm a Vehicle, but with these extras."

---

### Day 10 | Jan 12, 2026

**What I did:**  
Composition and class relationships. Built a Card/Deck system where Deck contains Card objects. Also practiced class methods and instance counting.

**Key insights:**

**1. Composition = objects containing objects:**  
Deck isn't a Card, it *has* Cards:
```python
class Deck:
    def __init__(self):
        self.cards = [Card(suit, val) for suit in suits for val in values]
```
52 Card objects live inside one Deck object.

**2. `__repr__` vs `__str__`:**  
`__repr__` is for developers (in lists, debugger):
```python
def __repr__(self):
    return f"{self.value} of {self.suit}"
# [Ace of Hearts, 2 of Hearts, ...]  <- shows nicely in lists
```

**3. `@classmethod` for alternative constructors:**  
When you want different ways to create an object:
```python
@classmethod
def from_dimensions(cls, length, width):
    return cls(length, width)

rect = Rectangle.from_dimensions(10, 5)
```
`cls` is the class itself, not an instance.

**4. `list.pop()` removes AND returns:**  
For dealing cards:
```python
def deal(self):
    return self.cards.pop()  # Returns last card, removes from deck
```
Deck shrinks as you deal. State changes naturally.

**Struggled with:**  
Initially confused `@classmethod` with `@staticmethod`. Classmethod gets the class (`cls`), staticmethod gets nothing—it's just a regular function namespaced inside the class.

**Realization:**  
Good class design mirrors real-world relationships. A deck contains cards, you deal from a deck, cards have suits and values. If your code structure matches the mental model, it's easier to reason about.

---

*Log entries will be added as I progress...*
