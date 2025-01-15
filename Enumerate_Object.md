---
title: "Enumerate Object"
author: "db"
---

# Characteristics
- An array containing items as group
- An ordered array
- An immutable array
- An __iterator__
- iterable
- not subscriptable

# Creating an Enumerate
```
animals = ['dog', 'cat', 'pig']
enumerate(animals, 1)
list(enumerate(animals, 2))
```

__Indexing and Slicing not working__

# Checking Element in an Enumerate
```
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
bkk = [e, 1, 2]
(1, 'dog') in bkk
(1, 'dog') in e
e in bkk
```

# Using Enumerate in a For Loop
1. manner
```
animals = ['dog', 'cat', 'bird']
e = enumerate(animals, 1)
for i, animal in e:
    print(i, ':', animal)
```
2. manner
```
animals = ['dog', 'cat', 'bird']
e = enumerate(animals, 1)
for pair in e:
    print(pair)
```

# Only be Iterated Once
## Iteration with For Loop
```
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
for i, animal in e:
    print(i, ':', animal)
list(e)
# solution 1: duplicate an enumerate
# solution 2: covert it to list or tuple
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
t = tuple(e)
for i in t:
    for j in i:
        print(j, end=' ')
    print()
```
## Iteration with list, tuple, set, dict
Constructors iterate an enumerate object and make it empty
```
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
list(e)
list(e)
```
## Iteration with the __in__ Operator
The __in__ operator iterates over the element and consume the iterator till the found element
```
# first element
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
(1, 'dog') in e
list(e)
# first and second element
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
(2, 'cat') in e
list(e)
# all element
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
(5, 'horse') in e
list(e)
```

