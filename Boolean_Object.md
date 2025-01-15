---
title: "Boolean Object"
author: "db"
---

# Characteristics
- Only two values: True and False
- Boolean object is a return from comparison operator

# Creating a Boolean Object

```
b = True
b = False
2 > 1
a, b = 0.01, 0.1**2 ; a == b
```

## Converting
- explizit converting
```
0, 0.0, '', [], (), {}, ({}), None: equal False
bool(1)
```
- implizit converting
```
1 * True
1 ** False
1 + True
1 - False
2 / True
```

# Logic Operator
1. not, and, or
```
not False
not 0
True and True
True and 2
1 and -2
-2 and []
0 and ()
True or False
True or ()
() or 0
1 or []
```
2. Precedence
    binary operator > comparison operator > logic operator
```
2 + 1 > 2 and True
1 + 1 > 2 and True
not 1 + 1 > 2 and False
not 1 + 1 > 2 and True
not 1 + 1 > 2 and True and False
```
    It runs from left to right many times until it finishes.
    1. run: not 2 > 2 and True and False
    2. run: not False and True and False
    3. run: True and True and False
    4. run: True and False
    5. run: False
3. Short-circuited
```
False and abcdef
```
4. any and all
```
a = [1, '', 2]
all(a)
any(a)
```












