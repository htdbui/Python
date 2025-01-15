# If
```
a = 5
if a >= 6:
    print('a is larger than or equal to 6')
elif a <= 4:
    print('a is smaller than or equal to 4')
else:
    print('a is 5')
```

# For Loop
- A first simple example
```
list_fruit = ['apple', 'mango', 'banana']
for fruit in list_fruit:
    print(fruit, end='\n')
```
- A nested for loop
```
list_names = ['Nam', 'Lan', 'Khoa']
for name in list_names:
    for letter in name:
        print(letter.upper(), end='.')
    print()
```
- For loop with else
```
# Finding the first negativ number in the list
alist = [2,3,5]
for i, a in enumerate(alist):
    if a < 0:
        print(f'{a} occurs at index {i}')
        break
else:
    print('no negative numbers at all')
```

# While Loop
- A first simple example
```
a = 0
while a < 10:
    print(a, end=', ')
    a += 3
```
- An example of Fibonacci sequence:
```
a, b = 0, 1
while a < 100:
    print(a, end=', ')
    a, b = b, a+b
```
- An example of finding the greatest common divisor
```
a, b = 1071, 462
while b:
    a, b = b, a%b
print(a)
```
- While loop with else
```
# finding the largest factor of a number
a=89; b=a-1
while b != 1:
    if not a%b:
        print(f'{b} is the largest factor of {a}')
        break
    b -= 1
else:
    print(f'{a} is a prime')
```

# break, continue, pass
- break
```
# finding the first negative number in a list
alist = [1,2,-1,2]
for i, a in enumerate(alist):
    if a < 0:
        break
print(f'{a} occurs at index {i}')
```
- continue
```
# finding even numbers till a maximum
for i in range(1, 11):
    if i%2:
        continue
    print(f'{i} is even')
```
- pass
```
# using for process of programming
for i in range(11):
    if i == 6:
        pass # do something special if the number is 6
    if not i%3:
        print(f'{i} is divisible by 3')
```
