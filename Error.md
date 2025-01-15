---
title: "Error"
author: "db"
---

# SyntaxError
- Characteristics
    - Mistakes in the grammar of the language
    - Caught by the Python compiler
    - Message indicates where the error occurred
    - Cannot overcome, have to repair the code
```
for lambda in range(3):
for f in range(3:
a = [1,2
if a = 5
if a == 5:
a*2 # IndentationError
```
# Exception
- Characteristics
    - runtime error
    - caused by attempting an invalid operation
    - solution: catch them
## Built-in Exception
    - FileNotFoundError
    - IndexError: [1, 2][2]
    - KeyError: key in dict not exist
    - NameError: variable not defined
    - TypeError: '00' + 7
    - ValueError: int('bay')
    - ZeroDivisionError: 2/0
    - SystemExit
## Customized Exception
```
class OurDefinedError(Exception):
    def __init__(self, code):
        self.code = code
    def __str__(self):
        return repr(self.code)
raise OurDefinedError('A message')
```
## Handling Exceptions

    It is Easier to Ask Forgiveness than to seek Permission (EAFP)
    
1. Example
```
try:
    1 / 0
    print('Is it executed?')
except ZeroDivisionError:
    print('1/0 is not defined')
```
2. Example
```
try:
    1 / x
    print('Is it executed?')
except (ZeroDivisionError, NameError):
    print('x is 0 or x is not defined')
```
3. Example
```
try:
    1 / x
    print('Is it executed?')
except:
    print('All exception are catched')
```

__Advanced__ <br>
try...except can take two clauses: <br>
    - else is executed if the exception is not raised <br>
    - finally is always excuted <br>
        
4. Example
```
def check_number(n):
    try:
        1 / n
    except ZeroDivisionError:
        print('This number is 0')
        return
    else:
        print(f'1/{n} = {1/n}')
    finally:
        print(f'Done with {n}')
    print(f'The next number: {n+1}')
    return
```
## Raising Exception
1. Example
```
n = 'abc'
if type(n) != 'int':
    raise TypeError('n must be an integer!')
```
2. Example
```
n = 3
if n%2:
    raise ValueError('n must be even!')
```

__assert__ will raise an AssertionError if the condition is not True

3. Example
```
def add_2e_vector(a,b):
    assert len(a) == len(b), 'Vectors a and b must have same length'
    assert len(a) == 2, 'Vectors a and b must have two elements'
    c = [None]*2
    c[0] = a[0] + b[0]
    c[1] = a[1] + b[1]
    return c
```

# Syntax Errors
- Characteristics
    - Mistakes in the grammar of the language
    - Caught by the Python compiler
    - Message indicates where the error occurred
    - Cannot overcome, have to repair the code

```python
for lambda in range(8):
```

		  Cell In [1], line 1
			for lambda in range(8):
				^
		SyntaxError: invalid syntax

```python
for f in range(8:
```

		  Cell In [3], line 1
			for f in range(8:
							^
		SyntaxError: invalid syntax

```python
a = [1, 2, 3
b = 4
```

		  Cell In [4], line 1
			a = [1, 2, 3
				^
		SyntaxError: '[' was never closed

```python
if a = 5:
```

		  Cell In [5], line 1
			if a = 5:
			   ^
		SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?

```python
a = 5
if a == 5:
a += 1
```

      Cell In [7], line 3
        a += 1
        ^
    IndentationError: expected an indented block after 'if' statement on line 2

# Exceptions
- Characteristics
    - runtime errors
    - caused by attempting an invalid operation
    - can be dealt with by catching them and not interupt the flow of executions.

## Built-in Exceptions
- FileNotFoundError: file or directory not exist such as OSError, IOError
- IndexError: \[1, 2\]\[2\]
- KeyError: key in dictionary not exist
- NameError: variable not defined
- TypeError: '00' + 7
- ValueError: int('7.0'); int(float('7.0'))
- ZeroDivisionError: 2/0
- SystemExit

## Customized Exceptions
- An simple example

```python
class OurDefinedError(Exception):
    def __init__(self, code):
        self.code = code
    def __str__(self):
        return repr(self.code)
n = 3
if n % 2:
    raise OurDefinedError('n must be even!')
```

		OurDefinedError                           Traceback (most recent call last)

		Cell In [12], line 8
			  6 n = 3
			  7 if n % 2:
		----> 8     raise OurDefinedError('n must be even!')


		OurDefinedError: 'n must be even!'

## Handling Exceptions
- "It is Easier to Ask Forgiveness than to seek Permission" (EAFP)

```python
x = 0
try:
    y = 1 / x
    print('1/', x, '=', y)
except ZeroDivisionError:
    print('1/0 is not defined')
```
    1/0 is not defined

```python
try:
    y = 1 / x
    print('1/', x, '=', y)
except (ZeroDivisionError, NameError):
    print('x is 0 or not defined')
```

    x is 0 or not defined

```python
x = 2
try:
    y = 1 / x
    print(f'1/{x}', '=', y)
except (ZeroDivisionError, NameError):
    print('x is 0 or not defined')
```

    1/2 = 0.5

```python
#for all exceptions
try:
    1 / xyz
except:
    pass 
```

try ... except can take two clauses:
- both have to follow except
- else is executed if the exception is not raised
- finally is always excuted


```python
def checking_number(n):
    try:
        x = 1 / n
    except ZeroDivisionError:
        print('n is 0')
        return
    else:
        print(f'1/{n}', '=', '{:.3f}'.format(x))
    finally:
        print(f'Done with the number {n}')

    print(f'The next number is {n+1}')

    return
```


```python
checking_number(0)
```

    n is 0
    Done with the number 0

```python
checking_number(3)
```
    1/3 = 0.333
    Done with the number 3
    The next number is 4

## Raising Exceptions


```python
n = 'abc'
if type(n) != 'int':
    raise ValueError('n must an integer!')
```

		ValueError                                Traceback (most recent call last)

		Cell In [27], line 3
			  1 n = 'abc'
			  2 if type(n) != 'int':
		----> 3     raise ValueError('n must an integer!')


		ValueError: n must an integer!

```python
n = 3
if n % 2:
    raise ValueError('n must be even!')
```

			ValueError                                Traceback (most recent call last)

			Cell In [28], line 3
				  1 n = 3
				  2 if n % 2:
			----> 3     raise ValueError('n must be even!')


			ValueError: n must be even!


		assert will raise an AssertionError if the condition is not True


```python
def adding_3e_vector(a, b):
    assert len(a) == len(b), 'Vectors a, b must have same length'
    assert len(a) == 3, 'Vectors a, b must contain three elements'
    c = [None]*3
    c[0] = a[0] + b[0]
    c[1] = a[1] + b[1]
    c[2] = a[2] + b[2]
    return c
adding_3e_vector([1, 2], [1, 2, 3])
```

		AssertionError                            Traceback (most recent call last)

		Cell In [31], line 9
			  7     c[2] = a[2] + b[2]
			  8     return c
		----> 9 adding_3e_vector([1, 2], [1, 2, 3])
			 10 print(adding_3e_vector([1, 2], [3, 4]))


		Cell In [31], line 2, in adding_3e_vector(a, b)
			  1 def adding_3e_vector(a, b):
		----> 2     assert len(a) == len(b), 'Vectors a, b must have same length'
			  3     assert len(a) == 3, 'Vectors a, b must contain three elements'
			  4     c = [None]*3


		AssertionError: Vectors a, b must have same length

```python
adding_3e_vector([1, 2], [3, 4])
```
    
		AssertionError                            Traceback (most recent call last)

		Cell In [32], line 1
		----> 1 adding_3e_vector([1, 2], [3, 4])


		Cell In [31], line 3, in adding_3e_vector(a, b)
			  1 def adding_3e_vector(a, b):
			  2     assert len(a) == len(b), 'Vectors a, b must have same length'
		----> 3     assert len(a) == 3, 'Vectors a, b must contain three elements'
			  4     c = [None]*3
			  5     c[0] = a[0] + b[0]


		AssertionError: Vectors a, b must contain three elements

```python
adding_3e_vector([1, 2, 3], [3, 4, 5])
```

    [4, 6, 8]

