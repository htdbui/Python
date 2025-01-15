---
title: "Function Object"
author: "db"
---

# Characteristics
- A set of statements
- A first class object

# Defining a Function
```
def a_function(a):
    return a**2
# call a function
a_function(3)
a_function
```

# Documenting
```
def a_function(a, b):
    """return a sum of two numbers"""
    return a + b
# open the document
a_function.__doc__
?a_function # only in jupyter notebook
```

# Arguments
## Inserting
```
# positional
a_funtion(1, 2)
# keyword
a_function(b=1, a=2)
```
? mixed: be careful!
If we mix these two types of arguments, all the positional arguments must come first. It mean it take the first values for a.
```
# a_function(1, a=2) return TypeError: a_function() got multiple values for argument 'a'
# a_function(b=1, 2) return SyntaxError: positional argument follows keyword argument
# a_function(2, b=1) works correctly
```
## Default Value
```
default_unit = 'm'
def report_length(value, unit=default_unit):
    return f'The length is {value:.2f} {unit}'
report_length(1.23)
```
- Change the variable makes no changes to the function
```
default_unit = 'cm'
report_length(3.23)
```
- Special case for mutable type
```
def a_function(alist=[]):
    alist.append(7)
    return alist
a_function(), a_function(), a_function([8]), a_function()
```
## Passing Argument by what
- Arguments are references. They are passed by values.
- with immutable object
```
number = 1000
print( f'First check global:    number = {number}, id = {id(number)}' )

def function(zahl):
    print( f'First check function:  zahl   = {zahl}, id = {id(zahl)}' )
    number = 1000
    print( f'Second check function: number = {number}, id = {id(number)}' )

function(number)
print( f'Second check global:   number = {number}, id = {id(number)}' )
```
- with mutable object list and method append
```
alist = [1000, 2000, 3000]
print( f'First check global:    alist = {alist},       id = {id(alist)}' )

def function(bkk):
    print( f'First check function:  bkk   = {bkk},       id = {id(bkk)}' )
    bkk.append (4000)
    print( f'Second check function: bkk   = {bkk}, id = {id(bkk)}' )
    print( f'Check the last element (function): element = {bkk[-1]}, id = {id(bkk[-1])}' )
function(alist)
print( f'Second check global:   alist = {alist}, id = {id(alist)} ' )
print( f'Check the last element (global):   element = {alist[-1]}, id = {id(alist[-1])}' )
```
- with mutable object list and changing elements
```
alist = [1000, 2000, 3000]
print( f'First check global:    alist = {alist},       id = {id(alist)}' )

def function(bkk):
    print( f'First check function:  bkk   = {bkk},       id = {id(bkk)}' )
    alist[0] = 'mot ngan'
    print( f'Second check function: bkk   = {bkk}, id = {id(bkk)}' )
function(alist)
print( f'Second check global:   alist = {alist}, id = {id(alist)} ' )
```

# Recursive Functions
```
def factorial_function(n):
    if n == 1:
        return 1
    return n * factorial_function(n-1)
```

# Lambda Functions
- A type of anonymous function
- The executable body must be expression, not statement
- No loop
- It support the pargdigm of functional programming
1. Example:
```
f = lambda x: x**2 + 2
f(2)
```
2. Example:
```
f = lambda x,y: x**2 + 2*x*y +y**2
f(2., 3.)
```
3. Example:
```
f = lambda x: x**2 if x%2 else x+2
f(3)
```
4. Example: 
```
CONST = 123
alist_function = [lambda x: CONST, lambda x: x, lambda x: x**2, lambda x: x**3]
alist_function[2](3)
```
4. Example explained
```
def const(x):
    return CONST
def lin(x):
    return x
def square(x):
    return x**2
def cube(x):
    return x**3
alist_function = [const , lin , square , cube]
alist_function[2](3)
```
5. Example
```
people = [('Nam', 23), ('Lan', 21), ('Khoa', 32), ('An', 9)]
sorted(people)
sorted(people, key=lambda e: e[1])
```
