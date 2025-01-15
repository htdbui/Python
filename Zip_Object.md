---
title: "Zip Object"
author: "db"
---

# Characteristics
- An array containing items as group
- An ordered array
- An immutable array
- An __iterator__
- iterable
- not subscriptable

# Creating a Zip
```
names = ['Nam', 'Lan', 'Khoa']
sex = ['male', 'female', 'male']
age = [20, 9, 33]
zip(names, sex, age)
list(zip(names, sex, age))
```

__Indexing and Slicing not working__

# Checking Element in a Zip
```
z = zip(names, sex, age)
bkk = [z, 1, 2]
('Nam', 'male', 20) in z
('Nam', 'male', 20) in bkk
z in bkk
```

# Using Zip in a For Loop
1. manner
```
z = zip(names, sex, age)
for name, sex, age in z:
    print(f'{name} is {sex} and {age} years old')
```
2. manner
```
z = zip(names, sex, age)
for group in z:
    print(group)
```

# Only be Iterated Once
## Iteration with For Loop
```
z = zip(names, sex, age)
for group in z:
    print(group)
list(z)
# solution 1: duplicate a zip
# solution 2: convert it to a list or a tuple
z = zip(names, sex, age)
t = tuple(z)
for element in t:
    print(element)
```
## Iteration with list, tuple, set, dict
Constructors iterate a zip object and make it empty
```
z = zip(names, sex, age)
list(z)
list(z)
```
## Iteration with the __in__ Operator
The __in__ operator iterates over the element and consume the iterator till the found element
```
# first element
z = zip(names, sex, age)
('Nam', 'male', 20) in z
list(z)
# first and second element
z = zip(names, sex, age)
('Lan', 'female', 9) in z
list(z)
# all element
z = zip(names, sex, age)
('Long', 'male', 34) in z
list(z)
```
