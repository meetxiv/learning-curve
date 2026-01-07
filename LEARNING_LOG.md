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
- Used `sep` and `end` parameters in `print()` to format output—cleaner than string concatenation
- `sep` is used when multiple parameters are passed in the same `print()` function and `end` when communicating through multiple `print()` functions
- `.join()` is actually very flexible and can be used in scenarios creatively 
- Discovered `map()` + `split()` combo for converting user input strings to numeric tuples in one line: `tuple(map(int, input().split(',')))`
- Solved the dogs-chickens problem using constraint validation (legs must be even, within valid range) before calculation—learned to fail early
- Floor division (`//`) vs regular division matters for discrete quantities like counting glasses of milk
- Input validation isn't optional—added checks for impossible scenarios (like odd number of legs for animals)

**Struggled with:** Initially overcomplicated the chicken-dogs problem by approaching it with rule based constraints and even factorising the problem, later realised it is solvable with basic linear algebra.

THINKING ELEMENTARY SOLVES THE PROBLEM.

---

### Day 3 | Jan 5, 2026

**What I did:**  
Solved 15 miscellaneous Python problems covering lists, strings, dictionaries, and functional programming concepts (map, filter, reduce).

**Key insights:**
- `set()` is the fastest way to get unique elements from a list
- `*args` in function definitions is powerful—used it to merge an arbitrary number of dictionaries using `dict.update()` in a loop
- `*args` is a notation (can also be *anything) it is a tuple, while `**kwargs` is a dictionary
- `dict.get(key, 0)` pattern is essential for frequency counting (finding mode of words) without throwing KeyErrors
- List comprehensions make filtering (like extracting even numbers) much more readable than loops
- For histogram binning, integer division (`// 10 * 10`) is a clever trick to find the lower bound of a bin without complex if-else chains
- **Bag of Words:** Implemented a simple NLP model using dictionary frequency counting—realized this is the foundation of text vectorization
- **Functional Programming:**
  - `map()` with `lambda` can process multiple lists in parallel (e.g., `map(lambda x,y,z: x+y+z, l1, l2, l3)`)
  - `reduce()` is surprisingly elegant for flattening 2D lists (`reduce(lambda x,y: x+y, list_2d)`)
  - Chaining `filter()` and `map()` allows complex data transformations in a single readable line (filtering employees by grade -> extracting full names)

**Struggled with:**  
The histogram problem was tricky. I had to figure out how to dynamically generate bin ranges based on the input data's min/max values instead of hardcoding them. Also, getting comfortable with nested lambda functions took some trial and error.

---

### Day 4 | Jan 6, 2026

**What I did:**  
Solved 14 problems on conditionals and control flow—salary calculations, number theory (primes, Armstrong, Fibonacci), and even a robot movement tracker.


**1. Prime number optimization:**  
Instead of checking all numbers up to `n`, only check up to `√n`. If a number has a factor greater than its square root, it must also have one smaller than it. Reduced complexity from O(n) to O(√n).
```python
for num in range(2, int(n**0.5) + 1):  # not range(2, n)
```

**2. Digit extraction pattern:**  
To process each digit of a number without converting to string:
```python
while num > 0:
    digit = num % 10   # extract last digit
    num //= 10         # remove last digit
```
Used this for reversing numbers and checking Armstrong numbers. Pure math > string manipulation.

**3. State machines with dictionaries:**  
Built a robot tracker that maintains position using a dictionary as state:
```python
moves = {'U': 0, 'D': 0, 'L': 0, 'R': 0}
moves[direction] += distance
```
Much cleaner than multiple if-else chains or separate variables.

**4. Clock angle problem:**  
The minute hand moves 6° per minute (360°/60). The hour hand moves 0.5° per minute (30°/60). I spent hell lot of time on this problem scribbling calculations on paper trying tp find out methods and in the end this problem taught me to think in terms of rates, not positions.

**5. Multiple exit conditions in loops:**  
Combining `continue` (skip iteration) and `break` (exit loop) for complex conditions like "sum until 300, but skip multiples of 5."

**Struggled with:**  
The clock angle problem initially. I was calculating positions instead of relative movement. Had to step back and think about it mathematically—both hands start at 12, minute hand laps the hour hand. The angle is just the difference in their positions.

**Pattern I'm noticing:**  
Most "tricky" problems become simple once you identify the underlying math. Fibonacci is just addition with memory. Prime checking is about factors. Armstrong is digit extraction + power. The code is just translating math to syntax and the Clock problem is just rate determination.

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

*Log entries will be added as I progress...*
