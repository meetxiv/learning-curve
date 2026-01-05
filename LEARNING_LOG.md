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

*Log entries will be added as I progress...*
