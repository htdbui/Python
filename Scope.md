# Characteristics
- LEGB: local enclosed global built-ins

# An Simple Example
```
# creating variables with values in a function
def function():
    a = 5
    print(a, b)
# it look up to global for value of b
# function() # NameError: name 'b' is not defined
b = 2
function()
```

# global, nonlocal
- global
```
# creating a global variable
x = 1
# defining a function1 trying to modify / rebind x
def function1():
    x += 1
# function1() # UnboundLocalError: 'x' referenced before assignment
```
    - using global
```
x = 1
def function2():
    global x
    x += 1
function2()
```
- nonlocal: used for nested function
```
def outer():
    x = 1
    
    def inner():
        nonlocal x
        x += 1
        print(f'inner: {x}')
    inner()
    print(f'outer: {x}')
```

# A Confusing Example
```
x = 1
def outer():
    x = 2
    
    def inner():
        x = 3
        x += 1
        print(f'inner: {x}')
    
    inner()
    print(f'outer: {x}')
outer()
print(f'global: {x}')
# inner: 4
# outer: 2
# global: 1
```
- using global
```
x = 1
def outer():
    x = 2
    
    def inner():
        global x
        x += 1
        print(f'inner: {x}')
    
    inner()
    print(f'outer: {x}')
outer()
print(f'global: {x}')
# inner: 2
# outer: 2
# global: 2
```
- global vs. local
```
x = 1
def outer():
    x = 2
    
    def inner():
        x = 3
        global x
        x += 1
        print(f'inner: {x}')
    
    inner()
    print(f'outer: {x}')
# SyntaxError: name 'x' is assigned to before global declaration
```
