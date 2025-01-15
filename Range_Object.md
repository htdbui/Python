---
title: "Range Object"
author: "db"
---

# Characteristics
- An array
- An ordered array
- An immutable array
- Iterable
- Subscriptable
- A type of a generator object

# Creating a Range
    syntax: range(a0=0, n, stride=1)
```
range(3, 9, 3)
list(range(3, 9, 3))
```

# Indexing and Slicing
```
r = range(10)
r[1]
r[3:]
list(r[3:])
r[1] = 5 return TypeError. No support item assignment
```

# Checking Element in a Range
```
r = range(10, 2, -2)
8 in r
bkk = [r, 1, 2]
8 in bkk
r in bkk
```

# Using Range in a For Loop
    Example about fibonacci numbers
```
n = 30
fib = [1,1]
for i in range(2, n+1):
    fib.append(fib[i-1] + fib[i-2])
###
a, b, n = 1, 1, 30
print(a, b, end=' ')
for i in range(2, n+1):
    a, b = b, a+b
    print(b, end=' ')
```




