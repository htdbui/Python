---
title: "Dictionary Object"
author: "db"
---

# Characteristics
- An array
- An ordered array
- Mutable
- Iterable
- Subscriptable (indexing by keys)
- Unhashable because mutable
- Keys take always hashable objects
- Keys, Values, Items are iterable
- Keys, Values, Items are not subscriptable

# Creating a Dictionary
## 1. Method
    Empty dictionary
```
d0 = {}
d0 = dict()
```
    Normal dictionary
```
{1:10, 'abc':[True,False], (1,2):1+5j}
```
    It will take the last value for the repeated key
```
{1:10, 'abc':[True,False], (1,2):1+5j, 1:20}
```
## 2. Method: dict()
### ~ 1. Manner:
    Keys cannot take digits
```
dict(a=1, b=2)
```
### ~ 2. Manner:
    Keys can take digits
```
dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
```
    Using enumerate
```
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
dict(e)
```
    Using zip (only zip with length of 2)
```
names = ['Lan', 'Nam', 'Khoa']
sex = ['female', 'male', 'male']
age = [23, 25, 26]
dict(zip(names, sex, age)) is wrong
dict(zip(names, age))
```

# Indexing
- always use key to index
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d[1]
```
- assign by indexing
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d[2] = 20
d[(1,2)] = 2+5j
```

# Checking Elements in a Dictionary
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
1 in d
'abc' in d
(1,2) in d
(3,4) in d
```

# Using Dictionary in For Loop
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j ]] )
for k in d:
    f'key is {k} and value is {d[k]}'
```

# Methods
## Keys
    Keys are iterable, but not subscriptable
- get()
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d.get(1)
d.get(2)
d.get(2, 'This key doesn't exist')
```
- keys()
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d.keys()
type(d.keys())
d.keys()[0] is wrong
list(d.keys())
for k in d.keys():
    print(k)
```
?: keys don't behave like enumerates, zips, reversed
```
d_keys = d.keys()
for k in d_keys:
    print(k)
d_keys
```
## Values
    Values are iterable, but not subscriptable
- values()
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d.values()
type(d.values())
d.values()[0] is wrong
list(d.values())
for v in d.values():
    print(v)
```
?: values don't behave like enumerates, zips
```
d_values = d.values()
for v in d_values:
    print(v)
d_values
```
## Items
    Items are iterable, but not subscriptable
    - items()
```
d = dict( [[1,10], ['abc',[True,False]], [(1,2),1+5j]] )
d.items()
type(d.items())
d.items()[0]
list(d.items())
for it in d.items():
    print(it)
```
?: items don't behave like enumerates, zips
```
d_items = d.items()
for it in d_items:
    print(it)
d_items
```
- update()
```
d1 = {1:10, 'abc':[True,False], (1,2):1+5j}
d2 = dict(a=1, abc=2)
d1.update(d2)
```
- defaultdict
```
text = '22 333 1 22 333 4444 55555 22 333 4444 55555'
```
    Option 1:
```
word_lengths = {}
for word in text.split():
    try:
        word_lengths[len(word)] +=1
    except KeyError:
        word_lengths[len(word)] = 1
```
    Option 2:
```
from collections import defaultdict
word_lengths = defaultdict(int)
for word in text.split():
    word_length[len(word)] += 1
```

#  Hashable
- immutable
- string, tuple, number, range, enumerate, zip
- A hash id is an integer representing the identity of an object
- A hash id is unique and constant for each object during its lifetime
