---
title: "String Object"
author: "db"
---

# Characteristics
- An array
- Contain only characters
- Immutable
- Iterable
- Subscriptable

# Creating a String
```
s = 'abc' # abc is string literal
```
- An empty string
```
s0 = ''
s0 = str()
```
- Organize a long string with multiple lines
```
long_string = 'abc'\
'def'
long_string = ('abc'
'def')
```

# Converting
```
str(9)
str(9.2)
str([1,2])
str( ((())) )
str( [[[]]] )
```
# Method
## binary operator
```
'ab' + 'cd'
'a' * 3
```
## remove underscores
```
'_abc'.lstrip('_')
'abc*'.rstrip('*')
' abc '.strip()
```
## check the first or the last character
```
'abc'.endswith('c')
'abc'.startswith('b')
```
## convert to capitalization
```
'abc'.upper()
'Abc'.lower()
'abc'.title()
```
## format spaces
```
'123'.center(4, '*')
'1234'.center(5, '*')
'123'.center(5, '*')
'123'.center(6, '*')
'1234'.center(7, '*')
```
## find the index of the character
```
'ab_ac_ad'.index('a')
'ab \ncd'.index('c')
```
## change characters
    strings are immutable. The result is the new string.
``` 
'a bcd a'.replace('a', '*')
```
## split and join
```
'a b c d'.split()
'a_b_c d'.split('_')
'abcd'.split('') is wrong
'*'.join('||')
'**'.join(['||', '//'])
'***'.join(['\\', '||', '//'])
```
    iterable objects can be the argument for join. Don't need subscriptable
```
d = {'a':1, 'b':2}
'*'.join(d.keys())
```
## check whether strings contain only letters
```
'abc'.isalpha()
'abc1'.isalpha()
'abc@'.isalpha()
'a b c'.isalpha()
'a \nb \nc'.isalpha()
```
## check whether strings contain only digits
```
'123'.isdigit()
'123a'.isdigit()
'123@'.isdigit()
'1 2 3'.isdigit()
'1 \n2 \n3'.isdigit()
```

# String Formatting
## creat
```
'{} + {} = {}'.format(3, 5, 8)
```
## specify placeholders
```
person, age = 'Lan', 25
'{1} is the age of {0}'.format(age, person)
'{name} is {number} years old'.format(number=age, name=person)
'{name} is {} years old'.format(age, name=person)
```
## adjust alignment, define length
```
'_{0:8}_'.format(12345)
'_{:8}_'.format(12345)
'_{:<8}_'.format(12345)
'_{:>8}_'.format(12345)
'_{:^8}_'.format(12345)
'_{:*^8}_'.format(12345)
```
## formating in formating
```
'_{:*^{}}_'.format(12345, 8)
```

# Number Formatting
## not specify number type
```
'The number is {:6}'.format(1234)
'The number is {:*<6}'.format(1234)
```
## adjust alignment, define length, specify sign
```
'The number is {:+6}'.format(1234)
'The number is {:+06}'.format(1234)
'The number is {:-6}'.format(1234)
'The number is {:-06}'.format(1234)
'The number is {:+6}'.format(-1234)
'The number is {:+06}'.format(-1234)
'The number is {:-6}'.format(-1234)
'The number is {:-06}'.format(-1234)
# confusing result
'The number is {:0>6}'.format(-1234)
```
---
## decimal
```
'{:6d}'.format(1234) # decimal is default value
```
## fixed-point
```
'{:8.3f}'.format(-12.3)
'{:8.3f}'.format(12345.7)
'{:~>10.3f}'.format(12345.7) # 10 is the whole length
###
'{:3.3f}'.format(-12345.6)
'{:+3.3f}'.format(12345.6)
```
## scientific notation
```
'{:15.3e}'.format(12.4)
'{:15.3E}'.format(12.4)
```
## general format
    convert to scientific notation for very large and very small numbers
```
'{:g}'.format(123456789)
```
## binary
```
'{:b}'.format(0)
'{:b}'.format(1)
'{:b}'.format(2)
```
## octal
```
':o'.format(0)
':o'.format(7)
':o'.format(8)
':o'.format(16)
```
## hex
```
':x'.format(0)
':x'.format(9)
':x'.format(10)
':x'.format(15)
':x'.format(16)
```

# f-strings (formatted string literals)
```
name, age = 'Lan', 23
f'{name} is {age} years old.'
f'{name} has {30 - age} years till 30 years old.'
f'{name} is a {name.isalpha()} name'
number = 33.2
f'{number:8.3f}'
```

# Comparing between format string and f-string
```
show_name_age = 'Your are {name} and {age} years old'
show_name_age.format(age=25, name='Lan')
```

# Older C-style Formatting
```
name, age = 'Lan', 25
'Her name is %s.' % name
'%s is %d years old.' % (name, age)
```
