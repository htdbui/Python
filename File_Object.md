---
title: "File Object"
author: "db"
---

# Charateristics
- A file object
- The mode plays an important role

# Mode
- r: read-only
- w: write
- a: append
- r+: read and write
- rb, wb, ab, rb+: binary version

# Opening
```
file = open('myfile.txt', 'r+')
```

# Writing
For each time of opening, it writes from beginning of the text.
- Example 1:
```
a_file = open('myfile.txt', 'r+')
a_file.write('this is my file')
print('_abc', file = a_file)
```
- Example 2:
```
a_file = open('myfile.txt', 'r+')
for i in range(10):
    print(i, i**2, i**3, i**4, file = a_file)
```

# Closing
```
a_file = open('myfile.txt', 'r+')
a_file.close()
```

# Reading
- Creating data for a text file first
```
a_file = open('myfile.txt', 'r+')
for i in range(10):
    print(i, i**2, i**3, i**4, sep=',', file=a_file)
a_file.close()
```
- Reading a file
```
a_file = open('myfile.txt', 'r+')
for line in a_file.readlines():
    print(line, end='')
# complicated details
a_file = open('myfile.txt', 'r+')
squares, cubes, fourths = [], [], []
for line in a_file.readlines():
    fields = line.split(',')
    squares.append(fields[1])
    cubes.append(fields[2])
    fourths.append(fields[3])
```
