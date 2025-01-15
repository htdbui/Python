---
title: "Class"
author: "db"
---

# Characteristics
- Class is a blueprint for creating an object.
- An object holds data (attributes) and functions (methods).
- Object may have a relationship of hierarchy. There is a base class or an abstract class. Customized classes inherit attributes and methods of the base class. They can customize base on their inheritance.

# Defining a Class
- Create a class of a bank account with:

        attributes: customer, account_number, balance
        methods: deposit, withdraw, check_balance
```
class BankAccount:
    """ An abstract base class represents a bank account """
    currency = '$'
    def __init__(self, customer, account_number, balance=0):
        """Create the bank account class with customer name, account number, opening balance"""
        self.customer = customer
        self.account_number = account_number
        self.balance = balance
    def deposit(self, amount):
        """Deposit amount into the account"""
        if amount > 0:
            self.balance += amount
        else:
            print(f'Invalid deposit amount: {amount}')
    def withdraw(self, amount):
        """Withdraw amount from the account"""
        if amount > 0:
            if amount > self.balance:
                print('Insufficient funds')
            else:
                self.balance -= amount
        else:
            print(f'Invalid withdrawal amount: {amount}')
    def check_balance(self):
        """Print a statement of the account"""
        print(f'The customer {self.customer.name if hasattr(self.customer, "name") else self.customer} has {self.currency}{self.balance:.2f} in the account {self.account_number}')
# currency is class variable, self.customer, self.account_number, self.balance are instance variables
```
- Create a class of a customer with:
        
        attributes: name, address, date of birth
        method: get_age
```
from datetime import datetime
class Customer:
    """ A class represents a bank customer """
    def __init__(self, name, address, dob):
        self.name = name
        self.address = address
        self.dob = datetime.strptime(dob, '%Y-%m-%d')
        self.password = '1234'
    def get_age(self):
        """ Calculate and return the customer's age"""
        today = datetime.today()
        age = today.year - self.dob.year - ((self.dob.month, self.dob.day) < (today.month, today.day))
        return age
```

# Instantiating the Objects
```
account1 = BankAccount('Lan', 123, 1000)
customer1= Customer('Khoa', 'Bonn, Germany', '1991-7-3')
account2 = BankAccount(customer1, 234, 3200)
```
__account1__
```
account1.check_balance()
account1.deposit(500)
account1.check_balance()
account1.withdraw(2000)
```
__account2__
```
account2.check_balance()
account2.customer.address
account2.customer.get_age()
```

# Class Inheritance
    syntax class SubClass(BaseClass1, BaseClass2,...)
- A subclass of a saving account
```
class SavingsAccount(BankAccount):
    """ A class represents a savings account """
    def __init__(self, customer, account_number, balance=0, interest_rate):
        """ Initialize a savings account """
        self.interest_rate = interest_rate
        # refer to the base class
        super().__init__(customer, account_number, balance)
    
    def add_interest(self):
        """ Add interest to the account"""
        self.balance *= (1+self.interest_rate/100)
```
- A subclass of a current account
```
class CurrentAccount(BankAccount):
    """ A class represents a current (checking) account """
    def __init__(self, customer, account_number, balance=0, annual_fee, transaction_limit):
        """ Initialize a current account """
        self.annual_fee = annual_fee
        self.transaction_limit = transaction_limit
        super().__init__(customer, account_number, balance)
    def withdraw(self, amount):
        if amount < 0:
            return print(f'Invalid withdrawal amount: {amount}')
        if amount > self.balance:
            return print('Insufficient funds')
        if amount > self.transaction_limit:
            return print(f'{self.currency}{amount} exceeds the transaction limit of {self.currency}{self.transaction_limit}')
        self.balance -= amount
    def apply_annual_fee(self):
        """ Deduct the annual fee from the balance """
        self.balance = max(0, self.balance - self.annual_fee)
```

# Instantiating the Objects
```
s_account = SavingsAccount('Nam', 142, 1000, 5.5)
c_account = CurrentAccount('Lan', 741, 1000, 110, 500)
```
__s_account__
```
s_account.check_balance()
s_account.add_interest()
s_account.check_balance()
```
__c_account__
```
c_account.check_balance()
c_account.withdraw(600)
c_account.deposit(500)
c_account.check_balance()
c_account.apply_annual_fee()
c_account.check_balance()
```

# Special Methods
x__add__(y) : x + y <br>
x__sub__(y) : x - y <br>
x__mul__(y) : x * y <br>
x__truediv__(y) : x / y <br>
x__floordiv__(y) : x // y <br>
x__mod__(y) : x % y <br>
x__pow__(y) : x ** y <br>
x__neg__(y) : -x <br>
x__matmul__(y) : x @ y <br>
x__abs__(y) : abs(x) <br>
x__contains__(y) : y in x <br>
x__lt__(y) : y < x <br>
x__le__(y) : y <= x <br>
x__eq__(y) : y == x <br>
x__ne__(y) : y != x <br>
x__gt__(y) : y > x <br>
x__ge__(y) : y >= x <br>
x__str__(y) : str(x) # optional, for human-readable string <br>
x__repr__(y) : repr(x) # should always be defined, for complete information <br>
x__radd__(y) : y + x <br>
...

# An Example for Special Methods
```
import math
class Vector2D:  
    def __init__(self, x, y):
        self.x, self.y = x, y
    def __str__(self): 
        return f'{self.x}i + {self.y}j'
    def __repr__(self):        
        return repr((self.x, self.y))
    def dot(self, other):        
        if not isinstance(other, Vector2D):
            raise TypeError('Can only take dot product of two Vector2D objects')
        return self.x*other.x + self.y*other.y
    def __matmul__(self, other):        
        if not isinstance(other, Vector2D):
            raise TypeError('Can only take dot product of two Vector2D objects')
        return self.x*other.x + self.y*other.y
    def __add__(self, other):        
        return Vector2D(self.x+other.x, self.y+other.y)
    def __sub__(self, other):
        return Vector2D(self.x-other.x, self.y-other.y)
    def __mul__(self, scalar):        
        if isinstance(scalar, int) or isinstance(scalar, float):
            return Vector2D(self.x*scalar, self.y*scalar)
        raise NotImplementedError('Can only multiply a vector by a scalar')
    def __rmul__(self, scalar):        
        return self.__mul__(scalar)
    def __neg__(self):        
        return Vector2D(-self.x, -self.y)
    def __truediv__(self, scalar):        
        return Vector2D(self.x / scalar, self.y / scalar)
    def __mod__(self, scalar):        
        return Vector2D(self.x % scalar, self.y % scalar)
    def __abs__(self):      
        return math.sqrt(self.x**2 + self.y**2)
    def distance_to(self, other):        
        return abs(self - other)
    def to_polar(self):        
        return self.__abs__(), math.atan2(self.y, self.x)
```
__Version with docstring__
```
import math
class Vector2D:
    """ A two-dimensional vector with Cartesian coordinates. """
    def __init__(self, x, y):
        self.x, self.y = x, y
    def __str__(self):
        """Human-readable string representation of the vector."""
        return f'{self.x}i + {self.y}j'
    def __repr__(self):
        """Unambigious (rõ ràng) string representation of the vector."""
        return repr((self.x, self.y))
    def dot(self, other):
        """The scalar (dot) product of self and other. Both must be vectors."""
        if not isinstance(other, Vector2D):
            raise TypeError('Can only take dot product of two Vector2D objects')
        return self.x*other.x + self.y*other.y
    def __matmul__(self, other):
        """The scalar (dot) product of self and other. Both must be vectors."""
        if not isinstance(other, Vector2D):
            raise TypeError('Can only take dot product of two Vector2D objects')
        return self.x*other.x + self.y*other.y
    def __add__(self, other):
        """Vector addition."""
        return Vector2D(self.x+other.x, self.y+other.y)
    def __sub__(self, other):
        """Vector subtraction."""
        return Vector2D(self.x-other.x, self.y-other.y)
    def __mul__(self, scalar):
        """Multiplication of a vector by a scalar."""
        if isinstance(scalar, int) or isinstance(scalar, float):
            return Vector2D(self.x*scalar, self.y*scalar)
        raise NotImplementedError('Can only multiply a vector by a scalar')
    def __rmul__(self, scalar):
        """Reflected multiplication so vector * scalar also works."""
        return self.__mul__(scalar)
    def __neg__(self):
        """Negation of the vector (invert through origin)."""
        return Vector2D(-self.x, -self.y)
    def __truediv__(self, scalar):
        """True division of the vector by a scalar."""
        return Vector2D(self.x / scalar, self.y / scalar)
    def __mod__(self, scalar):
        """One way to implement modulus operation: for each component."""
        return Vector2D(self.x % scalar, self.y % scalar)
    def __abs__(self):
        """Absolute value (magnitude) of the vector."""
        return math.sqrt(self.x**2 + self.y**2)
    def distance_to(self, other):
        """The distance between vector self and other."""
        return abs(self - other)
    def to_polar(self):
        """Return the vector's components in polar coordinates."""
        return self.__abs__(), math.atan2(self.y, self.x)
```

__Explain__ if \_\_name_\_ == '\_\_main\_\_' <br>
There is a file my_module.py. Its codes is
```
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector2D(self.x + other.x, self.y + other.y)

if __name__ == '__main__':
    v1 = my_module.Vector2D(1, 2)
    v2 = my_module.Vector2D(3, 4)
    v3 = v1 + v2
    print(v3.x, v3.y)
```
There is a file run.py. It code is
```
import my_module
v1 = my_module.Vector2D(0, 1)
v2 = my_module.Vector2D(2, 3)
v3 = v1 + v2
print(v3.x, v3.y)
```
We run in Terminal: python run.py. It returns (2, 4) <br>
If the code in my_module.py is:
```
class Vector2D:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __add__(self, other):
        return Vector2D(self.x + other.x, self.y + other.y)
        
v1 = my_module.Vector2D(1, 2)
v2 = my_module.Vector2D(3, 4)
v3 = v1 + v2
print(v3.x, v3.y)
```
Then there is the error because v1, v2, v3, print(v3.x, v3.y) in my_module.py is runned not by itself but in run.py. <br>
The purpose of using if \__name__ == '\__main__' is to prevent code that is only needed when the file is run as the main program from being executed when the file is imported as a module in another program.