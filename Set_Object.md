---
title: "Set Object"
author: "db"
---

# Characteristics
- A collection
- An unordered collection
- All items are unique
- All items must be hashable
- Sets are unhashable because they are mutable

# Creating a Set
## 1. Method
    Empty set
```
{()}
set()
set([])
```
    Normal set
```
{1, 2, 3, 1}
{(1,2), 2, 2, 1, 'a', 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
{[1,2]} return TypeError because list is unhasable
```
## 2. Method
    Using constructor set which takes an iterable object
- Using list or tuple
```
set([(1,2), 2, 2, 1, 'a', 'a'])
```
- Using string
```
set('abc')
```
- Using range
```
set(range(5))
```
- Using enumerate
```
animals = ['dog', 'cat', 'pig']
e = enumerate(animals, 1)
set(e)
set([e, 1])
```
- Using zip
```
names = ['Lan', 'Nam', 'Khoa']
sex = ['female', 'male', 'male']
age = [20, 9, 33]
z = zip(names, sex, age)
set(z)
```

# Checking Element in a Set
```
s = {(1,2), 2, 2, 1, 'a', 'a', range(3), enumerate('abc'), zip(('abc', 'cde'))}
(1,2) in s
'a' in s
1 in s
range(3) in s
enumerate('abc') in s
zip(('abc', 'cde')) in s
```

# Using Set in For Loop
- An example of bad name
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
for s in s:
    print(s)
s # remain only the last element
```
- An example of correct name
```
s = {(1,2), 1, 'a', range(3), enumerate('abc')}
for element in s:
    print(element)
s
```

# Methods
## Adding Elements
- must take a hashable object
```
s1 = {()}
s1.add(1.0)
s2 = set()
s2.add(range(3))
s2.add([1,2]) returns TypeError because list is unhashable
```
## Removing Elements
### 1. Method: remove()
- return None. It removes the element.
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
s.remove(1)
s.remove(range(3))
s.remove(2) returns KeyError
```
### 2. Method: discard()
- return None. It removes the element.
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
s.discard('a')
s.discard(enumerate('abc'))
s.discard(5) don't return KeyError
```
- Note: the remove method is used to eliminate an element from a set, raising a KeyError if the element is not found. On the other hand, the discard method removes an element from a set if it exists, without raising any errors if the element is not present. Both methods serve the purpose of removing elements from sets, but remove raises an error while discard does not.
### 3. Method: pop()
- return None. It removes an arbitry element.
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
s.pop(-1) returns TypeError because pop() takes no arguments
s.pop()
```
### 4. Method: clear()
- return None. It removes all elements.
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
s.clear()
```
### 5. Method: difference
- return a set. The original set is unchanged.
```
s = {(1,2), 1, 'a', range(3), enumerate('abc'), zip(('abc', 'def'))}
s.difference( ((1,2), 1) )
```
## Set Operation
```
a, b, c, d = {1,2}, {1,2,3}, {2,3,4}, {5,6} 
```
## issubset()
- must take an iterable object
```
a.issubset(b)
a.issubset([1,3,2])
{1}.issubset([1])
```
## issuperset()
- must take an iterable object
```
b.issuperset(a)
b.issuperset((1,))
b.issuperset((1,2,3))
```
### union()
- must take an iterable object
```
b.union(c)
b.union(c).union(d)
b.union([4,5])
b.union(enumerate('abc'))
```
- using |
```
b | c
b | c | d
b | (4,5) return TypeError
b | {4,5}
`````
### intersection()
- must take an iterable object
```
a.intersection(b)
a.intersection(b).intersection(c)
a.intersection([1,2,3])
b.union(enumerate('123'))
```
- using &
```
a & b
a & b & c
b & (1,2,3) return TypeError
b & {1,2,3}
`````
### difference()
- must take an iterable object
```
b.difference(a)
b.difference((1,2))
b.difference(range(3))
```
- using -
```
b - a
b - (1,2) return TypeError
b - {1,2}
```
### symmetric difference
- must take an iterable object
```
b.symmetric_difference(c)
b.symmetric_difference((2,3,4))
b.symmetric_difference(range(3))
```
- using ^
```
b ^ c
b ^ (2,3,4) return TypeError
b ^ {2,3,4}
```
### isdisjoint()
- must take an iterable object
```
c.isdisjoint(b)
c.isdisjoint(d)
c.isdisjoint((8,9))
```
## Frozensets
- immutable
- hashable
- must take an iterable object
```
frozenset(enumerate('abc'))
```




