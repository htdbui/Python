---
title: "List Object"
author: "db"
---

# Characteristics
- An array
- An ordered array
- A mutable array
- A sequence object
- Can contain different data types
- Iterable
- Subscriptable
- Unhashable

# Creating a List

```
bkk = [1, 2, 'ba']
bkk = list( (1, 2, 'ba') )
bkk = list( [1, 2, 'ba'] )
```
    An empty list:
```
bkk0 = []
bkk0 = list()
```

# Indexing and Slicing
- Indexing
```
bkk = [1, 2, 'ba']
bkk[0]
MT = [[1,2,3],
      [4,5,6]]
MT[0][0]
```
- Slicing
```
bkk = [1, 2, 'ba']
bkk[-1::-1]
bkk[-1:0:-1]
```

# Checking Element in a List
```
bkk1 = [1, 2, 'ba']
bkk2 = [bkk1, 4]
1 in bkk1
1 in bkk2
bkk1 in bkk2
```

# Mutability
1. case
```
bkk1 = [1, 2]
bkk2 = [bkk1, 3]
bkk1[0] = 'mot'
bkk2
```
2. case
```
bkk1 = bkk2 = [1, 2]
bkk1[0] = 'mot'
bkk2
```
3. case: example for copying a pointer
```
a = 3
bkk = [1, 2, a]
a = 4
bkk
```
4. case: slicing makes a new list but the same pointer
```
bkk1 = [1000, 2000]
bkk2 = bkk1[:]
bkk1[0] = 'mot ngan'
bkk2
```
5. case: constructor makes a new list but the same pointer
```
bkk1 = [1000, 2000]
bkk2 = list(bkk1)
bkk1[0] = 'mot ngan'
bkk2
```
6. case: copy method makes a new list but the same pointer
```
bkk1 = [1000, 2000]
bkk2 = bkk1.copy()
bkk1[0] = 'mot ngan'
bkk2
```

# Methods
## Adding elements to a list
1. method <br>
append() returns None. It changes the list.
```    
bkk = [1, 2]
bkk.append(3)
print(bkk)
bkk.append([4, 5])
```        
2. method <br>
extend() returns None. It changes the list. It requires an iterable argument, such as string, list, tuple, range, enumerate, zip.
```        
bkk = [1, 2]
bkk.extend([3])
# bkk.extend(3) is wrong
bkk.extend([4, 5])
```
__comparing append() and extend()__
```
bkk = [1, 2]
bkk.append('ab')
print(bkk)
bkk.extend('ab')
```
3. method <br>
insert() returns None. It adds a new element into the pointed position
```        
bkk = [1, 2]
bkk.insert(0, 'zero')
```        
4. method: binary operators
```        
bkk = [1, 2]
bkk + [3]
bkk * 3
```        
5. method: avoid this wrong one
```        
bkk = [1, 2]
bkk[2] = 3
```        
## Removing elements
1. method: <br>
pop() returns the removed element. It changes the list. It taks only one argument which is the position of the removed element.
```        
bkk = [1, 2, 3]
bkk.pop(0)
bkk.pop()
```        
2. method: <br>
remove() returns None. It changes the list by deleting the element.
```    
bkk = [1, 2, 1]
bkk.remove(1) # remove the first element
```        
3. method: using del
```        
bkk = [1, 2, 3, 4, 5]
del bkk[0]
del bkk[1:3]
```
4. method: <br>
clear() returns None. It removes all items. The result list is an empty list.
```
bkk = [1, 2, 3, 4, 5]
bkk.clear()
```
## Changing the order
1. method: sort and sorted <br>
sort() returns None. It changes the order.
```
bkk = [3, 1, 4, 2, 5]
bkk.sort()
bkk.sort(reverse=True)
```
    sorted is the built-in function. It returns sorted result. It does not change the order.
```
bkk = [3, 1, 4, 2, 5]
sorted(bkk)
sorted(bkk, reverse=True)

string = 'ABC is a brand from Kao Sieu Luc'
sorted(string.split())
sorted(string.split(), key=str.lower)
```
2. method: reverse and reversed
```
bkk = [1, 2, 3, 4, 5]
bkk.reverse()
```
    reversed is the built-in function. It returns a list_reverseiterator. It does not change the order.
```
bkk = [1, 2, 3, 4, 5]
reversed(bkk)
list(reversed(bkk))
```
## Other method
    count() is used for counting the number of element
```
bkk = [1, 2, 1, 3]
bkk.count(1)
```
    index()
```
bkk = [1, 2, 3]
bkk.index(2)
```

# List Comprehension
1. example
```
alist = [1,2,3]
[e**2 for e in alist]
```
2. example
```
alist = [1, 2, 3]
[e**2 if e % 2 else e**3 for e in alist]
```
3. example
```
[x**3 for x in range(1, 5)]
```
4. example
```
[e.upper () for e in 'abc def']
```
5. example: flattening a nested list
```
alist = [[1,2,3], [4,5,6]]
[e2 + 1 for e1 in alist for e2 in e1]
```
6. example: a nested list
```
M = [[1,2,3], [4,5,6]]
MT = [[0, 0], [0, 0], [0, 0]]
for ir in range(2):
    for ic in range(3):
        MT[ic][ir] = M[ir][ic]
```
7. example: a nested list
```
M = [[1,2,3], [4,5,6]]
MT = []
for i in range(3):
    MT.append( [row[i] for row in M] )
```
8. example: a nested list
```
M = [[1,2,3], [4,5,6]]
MT = [ [row[i] for row in M] for i in range(3) ]
```











