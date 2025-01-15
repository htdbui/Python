---
title: "Tuple Object"
author: "db"
---

# Charateristics
- An array
- An ordered array
- An immutable array
- A sequence object
- Can contain different data types
- Iterable
- Subscriptable
- Hashable

# Creating a Tuple
```
t = (1, 2, 'ba')
t = 1, 2, 'ba'
t = tuple([1, 2, 'ba']) # = tuple((1, 2, 'ba'))
```
    An empty tuple:
```
t0 = ()
t0 = tuple()
```
    A singleton is a tuple having only one element
```
t1 = (1,)
t1 = tuple([1]) # = tuple((1, ))
# tuple((1)) is wrong
```

# Indexing and Slicing
```
t = 1, 2, 'ba'
t[0]
t[-1::-1]
```

# Unpacking Elements of a Tuple
```
a, b, c = 1, 2, 'ba'
a, b, c = (1, 2, 'ba')
```

# Methods
- count()
```
t = 1, 2, 1, 'ba'
t.count(1)
```
- index()
```
t = 1, 2, 1, 'ba'
t.index(1)
t.index('ba')
```