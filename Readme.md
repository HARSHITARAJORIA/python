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
=============================
# Python String & List Operations Notes

## String Slicing & Indexing
```python
name = 'harshita'
print(name)                # harshita
slice_name = name[0:5]
print(slice_name)          # harsh
name[-1]                   # 'a'

num_list = "0123456789"
num_list[3:]               # '3456789'
num_list[:7]               # '0123456'
num_list[:7:2]             # '0246'
num_list[0:7:4]            # '04'
num_list[0:7:10]           # '0'
```

## String Methods
```python
username = "Harshita"
username.lower()           # 'harshita'
username.upper()           # 'HARSHITA'

name = '                        harshita'
name.strip()               # 'harshita'
print(name.replace('harshita', 'harshu'))  # '                        harshu'

name = "harshita rajoria girl"
print(name.split(" "))     # ['harshita', 'rajoria', 'girl']
print(name.find('h'))      # 0
print(name.find('s'))      # 3
print(name.count("h"))     # 2
print(name.count("a"))     # 4
print(name.count("g"))     # 1
print(name.count("girl"))  # 1
```

## String Formatting
```python
name = 'harshita'
age = 20
statement = "my {} is and my age is {}"
statement.format(name, age)    # 'my harshita is and my age is 20'
```

## Joining Strings
```python
names = ["harshita", "rajoria", "girl"]
print("".join(names))          # harshitarajoriagirl
print("#*#".join(names))       # harshita#*#rajoria#*#girl
print("_._".join(names))       # harshita_._rajoria_._girl
```

## Length
```python
len(name)                      # 8
len(names)                     # 3
```

## Iterating Over Strings
```python
for letter in name:
    print(letter)
# Output:
# h
# a
# r
# s
# h
# i
# t
# a
```

## String Quotes & Escape Characters
```python
name = "my name is 'harshita rajoria' "
name = 'my name is "harshita rajoria" '
name = "harshita\nrajoria"
print(name)
# Output:
# harshita
# rajoria
```

## Membership Test
```python
name = 'harshita rajoria'
("harshita" in name)           # True
("harshittta" in name)         #

======================
# Python List Operations & Control Flow Notes

## List Indexing & Slicing
```python
names = ['harshita', 'rajoria', 'cute', 'girl']
names[-1]           # 'girl'
names[0]            # 'harshita'
names[1:3]          # ['rajoria', 'cute']
```

## List Modification
```python
names[0] = 'vishnu'
names                  # ['vishnu', 'rajoria', 'cute', 'girl']

names[1:2] = 'yatisha'
names                  # ['vishnu', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute', 'girl']

names[1:1] = ['yasu', 'khushi']
names                  # ['vishnu', 'yasu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute', 'girl']
```

## Iterating Over Lists
```python
for i in names:
    print(i)
# Output:
# vishnu
# yasu
# khushi
# y
# a
# t
# i
# s
# h
# a
# cute
# girl

for i in names:
    print(i, end=" ")
# Output: vishnu yasu khushi y a t i s h a cute girl 
```

## Conditional Statements
```python
if 1 > 2:
    print("yes")    # (No output)

if 1 < 2:
    print(True)     # True

if 1 < 2:
    print(True)
else:
    print(False)    # True

if 1 < -2:
    print(True)
else:
    print(False)    # False
```

## Membership Test
```python
if "harsita" in names:
    print(True)     # (No output)

if "harshita" in names:
    print(True)     # (No output)

if "yasu" in names:
    print(True)     # True
```

## List Methods
```python
names.pop()         # 'girl'
names               # ['vishnu', 'yasu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute']

names.remove('yasu')
names               # ['vishnu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute']

names.insert(1, 'yasu')
names               # ['vishnu', 'yasu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute']
```

## List Copying & References
```python
names_copy = names
names_copy is names      # True

names_copy = names.copy()
names_copy is names      # False

names.append("mummy")
names_copy.append("papa")
names                   # ['vishnu', 'yasu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute', 'mummy']
names_copy              # ['vishnu', 'yasu', 'khushi', 'y', 'a', 't', 'i', 's', 'h', 'a', 'cute', 'papa']
```

## List Comprehension
```python
squared_num = [x**2 for x in range(10)]
squared_num            # [0, 1, 4, 9, 16, 25, 36, 49,