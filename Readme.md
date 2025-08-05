# Python

## Python Shell Notes

### Variables & Assignments
```python
name = 'harshita'
name = "harshita rajoria"
```
Strings can be enclosed in single or double quotes.  
Variable value can be reassigned.

### Basic Arithmetic Operations
```python
12 + 12      # 24
14 + 75      # 89
100 + 2      # 102
2.5 + 8      # 10.5
2.5 * 2      # 5.0
2 ** 10      # 1024
2 ** 1000    # Very large number (exponential calculation)
```

### 📌 Using the math Module
```python
math.pi
# Error: NameError → math not defined

import math
math.pi
# 3.141592653589793
```

### 📌 Using the random Module
```python
import random
random.random()                  # Random float between 0.0 and 1.0
random.choice([1, 2, 4, 7, 8])   # Random item from list
```

### 📌 String Operations
```python
usename = "harshita"

len(username)
# Error: NameError → username not defined

len(usename)      # 8
usename[0]        # 'h'
usename[-1]       # 'a'
usename[1:3]      # 'ar'
```

#### ❌ Common String Mistakes
```python
usename[len(usename)]
# IndexError: Index out of range

usename[0] = 'a'
# TypeError: Strings are immutable
```

### 📌 Using dir()
```python
dir(usename)
# Lists all string methods and dunder methods
```

## 📚 List Operations
```python
mylist = [1, 2, 3]
len(mylist)     # 3

mylist(0)
# TypeError: list object is not callable

mylist[0]       # 1
```

## 📚 Dictionary Operations
```python
myD = {
    'one': "lemon_tea",
    'two': "ginger_tea",
    'name': "amulya"
}
myD['one']       # 'lemon_tea'
```

#### ❌ Common Dictionary Mistakes
```python
myD = {'one':"lemon_tea","two":"ginger_tea","name":""amulya""}
# SyntaxError: improper use of quotes or missing comma

myD = {'one':"lemon_tea","two":"ginger_tea","nam":"a\
mylya"} 
# Incorrect multiline string usage — fixed by using triple quotes or correct line continuation
```

## 📚 Tuple Operations
```python
myTup = (1, 2, 3)
myTup[0]       # 1
myTup[1]       # 2
```

#### ❌ Tuple Error
```python
myTup[0]
# NameError: name 'myTup' is not defined (if used before declaring)
```

---

# Python Session Notes – Part 2

## 📌 System Module & Reference Count
```python
import sys

sys.getrefcount('harshita')           # 3
sys.getrefcount('har')                # 3
sys.getrefcount('harfhttttttttttttttttttt')  # 3
```
`sys.getrefcount()` gives the number of references to the object (includes temporary reference in argument).  
Even new-looking strings may return a reference count of 3 due to string interning.

## 🧠 Variable Assignments
```python
a = 'harshita'    # No error
a = 3.14          # Reassignment works
```
⚠️ Common Mistake:
```python
 a='harshita'
# IndentationError: unexpected indent
```
Leading whitespace not allowed unless inside a block (e.g., inside function/class).

## 📚 List Assignment and Mutability
```python
l1 = [1, 2, 3]
l2 = l1           # l2 references the same list
l1[0] = 100

# Result:
l1 → [100, 2, 3]
l2 → [100, 2, 3]
```
Both variables point to the same list object.

### 🔁 Creating New List with Same Content
```python
p1 = [1, 2, 3]
p2 = p1
p2 = [1, 2, 3]    # p2 now points to a different list
p1[0] = 100

# Result:
p1 → [100, 2, 3]
p2 → [1, 2, 3]
```
p2 is reassigned to a new list, breaking the reference to p1.

### ✂️ List Copy via Slicing
```python
h1 = [1, 2, 3]
h2 = h1[:]        # Creates a shallow copy

h1[0] = 100

# Result:
h1 → [100, 2, 3]
h2 → [1, 2, 3]
```

⚠️ Invalid Operation:
```python
h1 = {1, 2, 3}
h2 = h1[:]
# TypeError: 'set' object is not subscriptable
```
Sets are not indexable or sliceable.

## 🧬 Using copy Module
```python
import copy

h2 = copy.copy(h1)       # Shallow copy
h2 = copy.deepcopy(h1)   # Deep copy
```
- `copy.copy()` → New object, but nested objects are still references.
- `copy.deepcopy()` → Recursively copies everything (new object + new internals).

## 🧪 Identity vs Equality
```python
n = [1, 2, 3]
m = n

m == n     # True → Same content
m is n     # True → Same object

n = [1, 2, 3]  # Re-created
m == n         # True
m is n         # False → Now they are two different objects
```

---