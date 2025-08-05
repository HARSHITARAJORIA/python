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

# Python Shell Session Notes

## Basic Arithmetic & Types
```python
x = 2
y = 3
z = 4
x + y           # 5
x + y * z       # 14
40 + 2.45       # 42.45
int(40.85)      # 40
float(40)       # 40.0
'chai' + 'rajoria'  # 'chairajoria'
x, y, z         # (2, 3, 4)
x + 1, y * 2    # (3, 6)
y % 2           # 1
z ** 2          # 16
z ** 10         # 1048576
100             # 100
100 * 2         # 200
100 ** 2        # 10000
2 ** 1000       # Very large number
```

## String Operations
```python
str('chai')     # 'chai'
print('chai')   # chai
```

## Boolean Logic
```python
1 == 2 and 2 < 3    # False
1 == 2 or 2 < 3     # True
```

## Math Module
```python
import math
math.floor(3.4)     # 3
math.floor(-3.5)    # -4
math.ceil(8.6)      # 9
math.ceil(-8.6)     # -8
math.trunc(2.8)     # 2
math.trunc(-2.8)    # -2
```

## Large Integers
```python
999999999999999999999999999999999999999999 + 1
# 1000000000000000000000000000000000000000000

999999999999999999999999999999999999999999 * 99999999999999999999999 // 9999999999
# 999999999999999999999999999999998999999999000000000000000000000000000000001
```

## Complex Numbers
```python
2 + 1j           # (2+1j)
2 + 1j * 3       # (2+3j)
(2 + 1j) * 3     # (6+3j)
```

## Number Bases
```python
0o20             # 16
0xFF             # 255
0b1000           # 8
oct(45)          # '0o55'
hex(64)          # '0x40'
bin(64)          # '0b1000000'
int(64)          # 64
int('10', 2)     # 2
int('10', 8)     # 8
int('10', 16)    # 16
```

## Bitwise Operations
```python
x = 1
x << 2           # 4
x | 2            # 3
x & 2            # 0
```

## Random Module
```python
import random
random.randint(1, 10)    # Random integer between 1 and 10
l1 = ['harshita', 'vishnu', 'yatisha']
random.choice(l1)        # Random choice from list
random.shuffle(l1)       # Shuffle list in place
l1                      # Shuffled list
```

## Floating Point Precision
```python
0.1 + 0.1 + 0.1 - 0.3   # 5.551115123125783e-17
```

## Decimal & Fractions
```python
from decimal import Decimal
Decimal('0.1') + Decimal('0.2')   # Decimal('0.3')

from fractions import Fraction
myFra = Fraction(2, 7)
myFra                       # Fraction(2, 7)
```

## Sets & Types
```python
setone = {1, 2, 3, 4, 5, 1, 6}
setone                      # {1, 2, 3, 4, 5, 6}
type({})                    # <class 'dict'>
type(True)                  # <class 'bool'>
```

## Boolean & Integers
```python
True is 1                   # False (with SyntaxWarning)
True == 1                   # True
False == 0                  # True
True == 0                   # False
True + 1                    # 2
True + 10                   # 11
```

---