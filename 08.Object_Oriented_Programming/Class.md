# 🐍 Python Classes: The Complete Interactive Guide

> **Master Object-Oriented Programming in Python with Visual Examples and Real-World Applications**

[![Python class](https://img.shields.io/badge/Python-classes-blue?style=for-the-badge&logo=python&logoColor=white)](https://python.org)
![Topic](https://img.shields.io/badge/Topic-Object%20Oriented%20Programming-green?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-Beginner%20to%20Advanced-orange?style=for-the-badge)


---

```
 ██████╗██╗      █████╗ ███████╗███████╗███████╗███████╗
██╔════╝██║     ██╔══██╗██╔════╝██╔════╝██╔════╝██╔════╝
██║     ██║     ███████║███████╗███████╗█████╗  ███████╗
██║     ██║     ██╔══██║╚════██║╚════██║██╔══╝  ╚════██║
╚██████╗███████╗██║  ██║███████║███████║███████╗███████║
 ╚═════╝╚══════╝╚═╝  ╚═╝╚══════╝╚══════╝╚══════╝╚══════╝
```

---

## 📋 Table of Contents

- [🎯 What Are Python Classes?](#-what-are-python-classes)
- [🏗️ Class Anatomy & Structure](#️-class-anatomy--structure)
- [🛠️ Creating Your First Class](#️-creating-your-first-class)
- [🔧 Instance vs Class Variables](#-instance-vs-class-variables)
- [📦 Methods Deep Dive](#-methods-deep-dive)
- [🔒 Encapsulation & Privacy](#-encapsulation--privacy)
- [🌳 Inheritance & Polymorphism](#-inheritance--polymorphism)
- [✨ Special Methods (Dunder Methods)](#-special-methods-dunder-methods)
- [🎛️ Properties & Decorators](#️-properties--decorators)
- [🔬 Advanced Topics](#-advanced-topics)
- [🚀 Real-World Projects](#-real-world-projects)
- [💡 Best Practices](#-best-practices)
- [📝 Practice Exercises](#-practice-exercises)

---

## 🎯 What Are Python Classes?

Think of a **class** as a **blueprint** or **template** for creating objects. Just like an architectural blueprint defines how to build a house, a Python class defines the structure and behavior of objects.

```
🏗️ BLUEPRINT ANALOGY

    Blueprint (Class)          →         House (Object)
    ┌─────────────────┐                  ┌─────────────────┐
    │ • Rooms: 3      │       creates    │ • Address: 123  │
    │ • Color: _____  │        →         │ • Color: Blue   │
    │ • Windows: ___  │                  │ • Windows: 5    │
    │ • build()       │                  │ • build()       │
    └─────────────────┘                  └─────────────────┘
```

### 🔑 Key Benefits of Classes:

1. **🔄 Code Reusability**: Write once, use many times
2. **📦 Organization**: Group related data and functions together  
3. **🛡️ Encapsulation**: Hide implementation details
4. **🌱 Scalability**: Easy to extend and maintain
5. **🎯 Real-world Modeling**: Mirror real-world entities

---

## 🏗️ Class Anatomy & Structure

Let's dissect a Python class to understand its components:

```python
class Employee:  # ← Class Declaration (PascalCase naming)
    """A class to represent an Employee"""  # ← Docstring
    
    # Class Variables (shared by all instances)
    company = "TechCorp"
    total_employees = 0
    
    def __init__(self, name, salary):  # ← Constructor
        # Instance Variables (unique to each object)
        self.name = name
        self.salary = salary
        Employee.total_employees += 1
    
    def work(self):  # ← Instance Method
        return f"{self.name} is working"
    
    @classmethod  # ← Class Method
    def get_total_employees(cls):
        return cls.total_employees
    
    @staticmethod  # ← Static Method
    def is_workday(day):
        return day not in ['Saturday', 'Sunday']
```

### 📊 Visual Structure:

```
┌────────────────────────────────────────┐
│                 CLASS                  │
├────────────────────────────────────────┤
│ 📝 Docstring                           │
├────────────────────────────────────────┤
│ 🌍 Class Variables                     │
│   ├─ company = "TechCorp"              │
│   └─ total_employees = 0               │
├────────────────────────────────────────┤
│ 🏗️ Constructor (__init__)              │
│   ├─ self.name = name                  │
│   └─ self.salary = salary              │
├────────────────────────────────────────┤
│ ⚡ Instance Methods                    │
│   └─ work(self)                        │
├────────────────────────────────────────┤
│ 🏭 Class Methods                       │
│   └─ get_total_employees(cls)          │
├────────────────────────────────────────┤
│ 🔧 Static Methods                      │
│   └─ is_workday(day)                   │
└────────────────────────────────────────┘
```

---

## 🛠️ Creating Your First Class

Let's build a `Car` class step by step, following best practices:

### 📝 Step 1: Basic Class Definition

```python
class Car:
    """A simple car class for learning OOP concepts"""
    pass  # Placeholder - we'll add content next
```

### 🚗 Step 2: Adding the Constructor

```python
class Car:
    """A simple car class for learning OOP concepts"""
    
    # Class variables (shared by all cars)
    wheels = 4
    total_cars = 0
    
    def __init__(self, make, model, year, color="White"):
        """Initialize a new car instance"""
        # Instance variables (unique to each car)
        self.make = make
        self.model = model
        self.year = year
        self.color = color
        self.mileage = 0
        self.is_running = False
        
        # Increment total car count
        Car.total_cars += 1
        
        print(f"🚗 {year} {make} {model} created!")
```

### ⚡ Step 3: Adding Methods

```python
class Car:
    """A complete car class with methods and properties"""
    
    wheels = 4
    total_cars = 0
    
    def __init__(self, make, model, year, color="White"):
        self.make = make
        self.model = model
        self.year = year
        self.color = color
        self.mileage = 0
        self.is_running = False
        Car.total_cars += 1
        print(f"🚗 {year} {make} {model} created!")
    
    def start_engine(self):
        """Start the car engine"""
        if not self.is_running:
            self.is_running = True
            return f"🔥 {self.make} {self.model} engine started!"
        return f"⚠️ {self.make} {self.model} is already running!"
    
    def stop_engine(self):
        """Stop the car engine"""
        if self.is_running:
            self.is_running = False
            return f"🛑 {self.make} {self.model} engine stopped!"
        return f"⚠️ {self.make} {self.model} is already stopped!"
    
    def drive(self, miles):
        """Drive the car and update mileage"""
        if self.is_running:
            self.mileage += miles
            return f"🛣️ Drove {miles} miles. Total: {self.mileage} miles"
        return "❌ Start the engine first!"
    
    def get_info(self):
        """Return car information"""
        status = "Running 🏃" if self.is_running else "Stopped 🛑"
        return f"""
        🚗 Car Information:
        ├─ Make: {self.make}
        ├─ Model: {self.model}
        ├─ Year: {self.year}
        ├─ Color: {self.color}
        ├─ Mileage: {self.mileage:,} miles
        └─ Status: {status}
        """
    
    @classmethod
    def get_total_cars(cls):
        """Get total number of cars created"""
        return f"📊 Total cars created: {cls.total_cars}"
    
    @staticmethod
    def is_vintage(year):
        """Check if a car is vintage (>25 years old)"""
        from datetime import datetime
        current_year = datetime.now().year
        return current_year - year > 25

# 🎮 Interactive Demo
print("=== Creating Car Objects ===")
car1 = Car("Toyota", "Camry", 2020, "Red")
car2 = Car("Honda", "Civic", 2018, "Blue")
car3 = Car("Ford", "Mustang", 1965, "Yellow")

print("\n=== Testing Methods ===")
print(car1.start_engine())
print(car1.drive(100))
print(car1.get_info())

print("\n=== Class Methods ===")
print(Car.get_total_cars())

print("\n=== Static Methods ===")
print(f"Is 1965 Mustang vintage? {Car.is_vintage(1965)}")
print(f"Is 2020 Camry vintage? {Car.is_vintage(2020)}")
```

### 📊 Object Creation Process:

```
    Class Definition          Object Creation           Memory Layout
    ┌─────────────┐          ┌─────────────┐          ┌─────────────────┐
    │    Car      │   new    │   car1      │   ──→    │ Memory Address  │
    │             │   ───→   │             │          │ 0x7f8b8c0a8f40  │
    │ __init__()  │          │ make="Ford" │          ├─────────────────┤
    │ start()     │          │ model="F150"│          │ make: "Ford"    │
    │ drive()     │          │ year=2023   │          │ model: "F150"   │
    └─────────────┘          │ color="Red" │          │ year: 2023      │
                             └─────────────┘          │ color: "Red"    │
                                                      │ mileage: 0      │
                                                      │is_running: False│
                                                      └─────────────────┘
```

---

## 🔧 Instance vs Class Variables

Understanding the difference between instance and class variables is crucial:

### 🎯 Visual Comparison:

```
📊 VARIABLE SCOPE DIAGRAM

                    ┌─────────────────────────────────┐
                    │          CLASS LEVEL            │
┌─────────────────┐ │  ┌─────────┐  ┌─────────────┐   │
│  Class Vars     │ │  │ wheels  │  │total_cars   │   │
│ (Shared by all) │ │  │   = 4   │  │    = 3      │   │
└─────────────────┘ │  └─────────┘  └─────────────┘   │
                    └─────────────────────────────────┘
                              │           │
                              ▼           ▼
        ┌─────────────────┬─────────────────┬─────────────────┐
        │  INSTANCE 1     │  INSTANCE 2     │  INSTANCE 3     │
        │  ┌───────────┐  │  ┌───────────┐  │  ┌───────────┐  │
        │  │ make:     │  │  │ make:     │  │  │ make:     │  │
        │  │"Toyota"   │  │  │"Honda"    │  │  │"Ford"     │  │
        │  │ model:    │  │  │ model:    │  │  │ model:    │  │
        │  │"Camry"    │  │  │"Civic"    │  │  │"Mustang"  │  │
        │  │ year:2020 │  │  │ year:2018 │  │  │ year:1965 │  │
        │  │ color:    │  │  │ color:    │  │  │ color:    │  │
        │  │"Red"      │  │  │"Blue"     │  │  │"Yellow"   │  │
        │  └───────────┘  │  └───────────┘  │  └───────────┘  │
        └─────────────────┴─────────────────┴─────────────────┘
```

### 💡 Practical Example:

```python
class BankAccount:
    # 🏛️ Class Variables (shared by all accounts)
    bank_name = "Python Bank"
    interest_rate = 0.02
    total_accounts = 0
    
    def __init__(self, account_holder, initial_balance=0):
        # 👤 Instance Variables (unique to each account)
        self.account_holder = account_holder
        self.balance = initial_balance
        self.account_number = f"ACC{BankAccount.total_accounts + 1:04d}"
        BankAccount.total_accounts += 1
    
    def deposit(self, amount):
        self.balance += amount
        return f"💰 Deposited ${amount}. New balance: ${self.balance}"
    
    def withdraw(self, amount):
        if amount <= self.balance:
            self.balance -= amount
            return f"💸 Withdrew ${amount}. New balance: ${self.balance}"
        return "❌ Insufficient funds!"
    
    @classmethod
    def change_interest_rate(cls, new_rate):
        """Change interest rate for all accounts"""
        cls.interest_rate = new_rate
        return f"📊 Interest rate changed to {new_rate*100}% for all accounts"
    
    def apply_interest(self):
        """Apply interest to this specific account"""
        interest = self.balance * self.interest_rate
        self.balance += interest
        return f"💹 Interest of ${interest:.2f} applied. New balance: ${self.balance:.2f}"

# 🎮 Demo: Instance vs Class Variables
account1 = BankAccount("Alice", 1000)
account2 = BankAccount("Bob", 500)

print("=== Individual Balances (Instance Variables) ===")
print(f"Alice's balance: ${account1.balance}")
print(f"Bob's balance: ${account2.balance}")

print("\n=== Shared Information (Class Variables) ===")
print(f"Bank name: {BankAccount.bank_name}")
print(f"Interest rate: {BankAccount.interest_rate*100}%")
print(f"Total accounts: {BankAccount.total_accounts}")

print("\n=== Changing Class Variable Affects All ===")
print(BankAccount.change_interest_rate(0.03))
print(account1.apply_interest())
print(account2.apply_interest())
```

---

## 📦 Methods Deep Dive

Python classes support three types of methods, each with different purposes:

### 🔍 Method Types Overview:

```
┌─────────────────────────────────────────────────────────────────┐
│                        METHOD TYPES                             │
├─────────────────┬─────────────────┬─────────────────────────────┤
│ INSTANCE METHOD │  CLASS METHOD   │     STATIC METHOD           │
├─────────────────┼─────────────────┼─────────────────────────────┤
│ def method(self)│ @classmethod    │ @staticmethod               │
│                 │ def method(cls) │ def method(args)            │
├─────────────────┼─────────────────┼─────────────────────────────┤
│ • Has access to │ • Has access to │ • No access to self or cls  │
│   instance data │   class data    │ • Independent function      │
│ • Can modify    │ • Can modify    │ • Utility function          │
│   object state  │   class state   │ • Logically belongs to      │
│ • Most common   │ • Alternative   │   the class                 │
│                 │   constructors  │                             │
└─────────────────┴─────────────────┴─────────────────────────────┘
```

### 🛠️ Comprehensive Example:

```python
from datetime import datetime
import math

class Circle:
    """A comprehensive Circle class demonstrating all method types"""
    
    # Class variables
    pi = 3.14159
    total_circles = 0
    
    def __init__(self, radius):
        """Instance method - Constructor"""
        if radius <= 0:
            raise ValueError("Radius must be positive")
        self.radius = radius
        self.created_at = datetime.now()
        Circle.total_circles += 1
    
    # 🔵 INSTANCE METHODS (work with specific instances)
    def area(self):
        """Calculate area of this circle"""
        return Circle.pi * (self.radius ** 2)
    
    def circumference(self):
        """Calculate circumference of this circle"""
        return 2 * Circle.pi * self.radius
    
    def scale(self, factor):
        """Scale the radius by a factor"""
        self.radius *= factor
        return f"Circle scaled by {factor}x. New radius: {self.radius}"
    
    def is_larger_than(self, other_circle):
        """Compare with another circle"""
        return self.area() > other_circle.area()
    
    # 🏭 CLASS METHODS (work with class itself)
    @classmethod
    def from_diameter(cls, diameter):
        """Alternative constructor: create circle from diameter"""
        return cls(diameter / 2)
    
    @classmethod
    def from_area(cls, area):
        """Alternative constructor: create circle from area"""
        radius = math.sqrt(area / cls.pi)
        return cls(radius)
    
    @classmethod
    def get_stats(cls):
        """Get class statistics"""
        return f"Total circles created: {cls.total_circles}"
    
    @classmethod
    def change_pi_precision(cls, new_pi):
        """Change pi value for all circles"""
        cls.pi = new_pi
    
    # 🔧 STATIC METHODS (utility functions)
    @staticmethod
    def compare_areas(radius1, radius2):
        """Compare areas of two circles by radius (utility function)"""
        area1 = Circle.pi * (radius1 ** 2)
        area2 = Circle.pi * (radius2 ** 2)
        return f"Circle 1 area: {area1:.2f}, Circle 2 area: {area2:.2f}"
    
    @staticmethod
    def is_valid_radius(radius):
        """Check if radius is valid"""
        return isinstance(radius, (int, float)) and radius > 0
    
    @staticmethod
    def convert_units(radius, from_unit, to_unit):
        """Convert radius between units"""
        conversions = {
            'cm_to_m': 0.01,
            'm_to_cm': 100,
            'inch_to_cm': 2.54,
            'cm_to_inch': 0.393701
        }
        key = f"{from_unit}_to_{to_unit}"
        if key in conversions:
            return radius * conversions[key]
        return radius
    
    def __str__(self):
        """String representation"""
        return f"Circle(radius={self.radius}, area={self.area():.2f})"

# 🎮 Interactive Demonstration
print("=== Creating Circles with Different Methods ===")

# Regular constructor
circle1 = Circle(5)
print(f"Circle 1: {circle1}")

# Class method constructors
circle2 = Circle.from_diameter(10)
print(f"Circle 2 (from diameter): {circle2}")

circle3 = Circle.from_area(78.54)
print(f"Circle 3 (from area): {circle3}")

print(f"\n=== Instance Method Examples ===")
print(f"Circle 1 area: {circle1.area():.2f}")
print(f"Circle 1 circumference: {circle1.circumference():.2f}")
print(circle1.scale(2))
print(f"Circle 1 > Circle 2? {circle1.is_larger_than(circle2)}")

print(f"\n=== Class Method Examples ===")
print(Circle.get_stats())

print(f"\n=== Static Method Examples ===")
print(Circle.compare_areas(5, 3))
print(f"Is radius 5 valid? {Circle.is_valid_radius(5)}")
print(f"Is radius -2 valid? {Circle.is_valid_radius(-2)}")
print(f"Convert 5cm to inches: {Circle.convert_units(5, 'cm', 'inch'):.2f}")
```

### 🎯 When to Use Each Method Type:

```
┌─────────────────────────────────────────────────────────────────┐
│                      USAGE GUIDELINES                           │
├─────────────────┬───────────────────────────────────────────────┤
│ INSTANCE METHOD │ • Default choice for most operations          │
│                 │ • When you need access to instance data       │
│                 │ • Modifying object state                      │
│                 │ • Object-specific calculations                │
├─────────────────┼───────────────────────────────────────────────┤
│ CLASS METHOD    │ • Alternative constructors                    │
│                 │ • Factory methods                             │
│                 │ • Operations on class-level data              │ 
│                 │ • Getting class statistics                    │
├─────────────────┼───────────────────────────────────────────────┤
│ STATIC METHOD   │ • Utility functions related to the class      │
│                 │ • Validation functions                        │
│                 │ • Helper functions that don't need            │
│                 │   class or instance data                      │
│                 │ • Unit conversions                            │
└─────────────────┴───────────────────────────────────────────────┘
```

---

## 🔒 Encapsulation & Privacy

Python uses naming conventions to indicate the intended privacy level of attributes and methods:

### 🔐 Privacy Levels:

```
┌─────────────────────────────────────────────────────────────────┐
│                    PRIVACY CONVENTIONS                          │
├─────────────────┬───────────────────────────────────────────────┤
│ PUBLIC          │ name          ← Freely accessible             │
│ PROTECTED       │ _name         ← Internal use (convention)     │
│ PRIVATE         │ __name        ← Name mangling (enforced)      │
└─────────────────┴───────────────────────────────────────────────┘
```

### 🏦 Practical Example - Bank Account:

```python
class SecureBankAccount:
    """A bank account demonstrating encapsulation principles"""
    
    def __init__(self, account_holder, initial_balance=0, pin=1234):
        # Public attributes (accessible from outside)
        self.account_holder = account_holder
        self.account_type = "Savings"
        
        # Protected attributes (internal use, but accessible)
        self._account_number = self._generate_account_number()
        self._created_date = datetime.now()
        
        # Private attributes (name mangling applied)
        self.__balance = initial_balance  # Becomes _SecureBankAccount__balance
        self.__pin = pin                  # Becomes _SecureBankAccount__pin
        self.__transaction_history = []   # Private transaction log
    
    # Public methods (full access)
    def deposit(self, amount):
        """Public method to deposit money"""
        if self._validate_amount(amount):
            self.__balance += amount
            self.__log_transaction("DEPOSIT", amount)
            return f"✅ Deposited ${amount}. Balance: ${self.get_balance()}"
        return "❌ Invalid amount"
    
    def withdraw(self, amount, pin):
        """Public method to withdraw money (requires PIN)"""
        if not self._verify_pin(pin):
            return "❌ Incorrect PIN"
        
        if not self._validate_amount(amount):
            return "❌ Invalid amount"
        
        if amount > self.__balance:
            return "❌ Insufficient funds"
        
        self.__balance -= amount
        self.__log_transaction("WITHDRAWAL", amount)
        return f"✅ Withdrew ${amount}. Balance: ${self.get_balance()}"
    
    def get_balance(self):
        """Public method to get current balance"""
        return self.__balance
    
    def change_pin(self, old_pin, new_pin):
        """Public method to change PIN"""
        if self._verify_pin(old_pin):
            self.__pin = new_pin
            self.__log_transaction("PIN_CHANGE", 0)
            return "✅ PIN changed successfully"
        return "❌ Incorrect old PIN"
    
    # Protected methods (intended for internal use)
    def _generate_account_number(self):
        """Protected method to generate account number"""
        import random
        return f"ACC{random.randint(100000, 999999)}"
    
    def _validate_amount(self, amount):
        """Protected method to validate transaction amount"""
        return isinstance(amount, (int, float)) and amount > 0
    
    def _verify_pin(self, pin):
        """Protected method to verify PIN"""
        return pin == self.__pin
    
    # Private methods (name mangling applied)
    def __log_transaction(self, transaction_type, amount):
        """Private method to log transactions"""
        transaction = {
            'type': transaction_type,
            'amount': amount,
            'timestamp': datetime.now(),
            'balance_after': self.__balance
        }
        self.__transaction_history.append(transaction)
    
    def __get_transaction_history(self):
        """Private method to get transaction history"""
        return self.__transaction_history
    
    # Property to safely access transaction history
    @property
    def transaction_count(self):
        """Public property to get number of transactions"""
        return len(self.__transaction_history)
    
    def __str__(self):
        return f"Account({self.account_holder}, {self._account_number})"

# 🎮 Demonstration of Encapsulation
print("=== Creating Secure Bank Account ===")
account = SecureBankAccount("Alice", 1000, 1234)

print(f"Account holder: {account.account_holder}")  # Public - OK
print(f"Account number: {account._account_number}") # Protected - accessible but not recommended

print("\n=== Testing Public Methods ===")
print(account.deposit(500))
print(account.withdraw(200, 1234))
print(account.change_pin(1234, 5678))

print("\n=== Accessing Private Attributes (Demonstration) ===")
# This won't work - attribute doesn't exist
try:
    print(account.__balance)
except AttributeError as e:
    print(f"❌ Direct access failed: {e}")

# But name mangling makes it accessible (not recommended!)
try:
    print(f"⚠️ Name mangled access: ${account._SecureBankAccount__balance}")
except AttributeError as e:
    print(f"❌ Even name mangled access failed: {e}")

print(f"✅ Proper access through property: {account.transaction_count} transactions")
```

### 🔍 Name Mangling Visualization:

```
┌─────────────────────────────────────────────────────────────────┐
│                      NAME MANGLING                              │
├─────────────────────────────────────────────────────────────────┤
│  Class Definition      →      Actual Attribute Name             │
├─────────────────────────────────────────────────────────────────┤
│  class MyClass:                                                 │
│      __private_var  →  _MyClass__private_var                    │
│      __method()     →  _MyClass__method()                       │
│                                                                 │
│  Purpose: Prevent accidental access and name conflicts          │
│  Note: Not true privacy - still accessible if you know the      │
│        mangled name                                             │
└─────────────────────────────────────────────────────────────────┘
```

---

## 🌳 Inheritance & Polymorphism

Inheritance allows you to create new classes based on existing ones, promoting code reuse and establishing relationships between classes.

### 🏗️ Inheritance Types:

```
┌─────────────────────────────────────────────────────────────────┐
│                    INHERITANCE HIERARCHY                        │
└─────────────────────────────────────────────────────────────────┘

1️⃣ SINGLE INHERITANCE        2️⃣ MULTIPLE INHERITANCE
   ┌─────────────┐              ┌──────────┐ ┌──────────┐
   │   Parent    │              │ Parent1  │ │ Parent2  │
   └─────────────┘              └──────────┘ └──────────┘
          │                           └─────┬─────┘
          ▼                                 ▼
   ┌─────────────┐                   ┌──────────┐
   │    Child    │                   │  Child   │
   └─────────────┘                   └──────────┘

3️⃣ MULTILEVEL INHERITANCE     4️⃣ HIERARCHICAL INHERITANCE
   ┌─────────────┐                   ┌─────────────┐
   │ Grandparent │                   │   Parent    │
   └─────────────┘                   └─────────────┘
          │                                │
          ▼                        ┌───────┴───────┐
   ┌─────────────┐                 ▼               ▼
   │   Parent    │          ┌─────────────┐ ┌─────────────┐
   └─────────────┘          │   Child1    │ │   Child2    │
          │                 └─────────────┘ └─────────────┘
          ▼
   ┌─────────────┐
   │    Child    │
   └─────────────┘
```

### 🎮 Comprehensive Example - Game Characters:

```python
# 👑 Base class (Parent)
class Character:
    """Base class for all game characters"""
    
    def __init__(self, name, health=100, level=1):
        self.name = name
        self.health = health
        self.max_health = health
        self.level = level
        self.experience = 0
        self.skills = []
    
    def take_damage(self, damage):
        """Take damage and update health"""
        self.health = max(0, self.health - damage)
        status = "💀 Defeated" if self.health == 0 else f"❤️ {self.health}/{self.max_health} HP"
        return f"{self.name} took {damage} damage! {status}"
    
    def heal(self, amount):
        """Heal character"""
        old_health = self.health
        self.health = min(self.max_health, self.health + amount)
        healed = self.health - old_health
        return f"✨ {self.name} healed for {healed} HP! ({self.health}/{self.max_health})"
    
    def gain_experience(self, exp):
        """Gain experience and potentially level up"""
        self.experience += exp
        if self.experience >= self.level * 100:
            return self.level_up()
        return f"📈 {self.name} gained {exp} XP! ({self.experience}/{self.level * 100})"
    
    def level_up(self):
        """Level up character"""
        self.level += 1
        self.experience = 0
        self.max_health += 20
        self.health = self.max_health
        return f"🎉 {self.name} leveled up to level {self.level}!"
    
    def display_stats(self):
        """Display character statistics"""
        return f"""
        🎭 {self.__class__.__name__}: {self.name}
        ├─ Level: {self.level}
        ├─ Health: {self.health}/{self.max_health}
        ├─ Experience: {self.experience}/{self.level * 100}
        └─ Skills: {', '.join(self.skills) if self.skills else 'None'}
        """
    
    # Virtual method to be overridden by subclasses
    def attack(self):
        """Basic attack - to be overridden"""
        return f"⚔️ {self.name} performs a basic attack!"

# 🗡️ Warrior class (Single Inheritance)
class Warrior(Character):
    """Warrior class inheriting from Character"""
    
    def __init__(self, name, health=150):
        super().__init__(name, health)  # Call parent constructor
        self.weapon = "Iron Sword"
        self.armor = "Leather Armor"
        self.skills = ["Sword Mastery", "Shield Block"]
        self.rage = 0
    
    def attack(self):  # Method overriding
        """Warrior's powerful attack"""
        damage = 25 + (self.level * 5)
        self.rage = min(100, self.rage + 10)
        return f"⚔️ {self.name} swings {self.weapon} for {damage} damage! (Rage: {self.rage}/100)"
    
    def berserker_rage(self):
        """Special warrior ability"""
        if self.rage >= 50:
            self.rage = 0
            damage = 50 + (self.level * 10)
            return f"💀 {self.name} enters BERSERKER RAGE! Deals {damage} massive damage!"
        return f"❌ {self.name} needs more rage (current: {self.rage}/50)"
    
    def equip_weapon(self, weapon):
        """Equip a new weapon"""
        old_weapon = self.weapon
        self.weapon = weapon
        return f"🔄 {self.name} equipped {weapon} (was {old_weapon})"

# 🔮 Mage class (Single Inheritance)
class Mage(Character):
    """Mage class inheriting from Character"""
    
    def __init__(self, name, health=80):
        super().__init__(name, health)
        self.mana = 100
        self.max_mana = 100
        self.spell_book = ["Fireball", "Heal", "Lightning Bolt"]
        self.skills = ["Spell Casting", "Mana Control"]
    
    def attack(self):  # Method overriding
        """Mage's magical attack"""
        if self.mana >= 20:
            self.mana -= 20
            damage = 30 + (self.level * 7)
            return f"🔥 {self.name} casts Fireball for {damage} damage! (Mana: {self.mana}/{self.max_mana})"
        return f"❌ {self.name} is out of mana!"
    
    def cast_heal(self):
        """Special healing spell"""
        if self.mana >= 30:
            self.mana -= 30
            heal_amount = 40 + (self.level * 5)
            return self.heal(heal_amount) + f" (Mana: {self.mana}/{self.max_mana})"
        return f"❌ {self.name} needs 30 mana to cast heal!"
    
    def meditate(self):
        """Restore mana"""
        restored = min(30, self.max_mana - self.mana)
        self.mana += restored
        return f"🧘 {self.name} meditated and restored {restored} mana! ({self.mana}/{self.max_mana})"

# 🏹 Archer class (Single Inheritance)
class Archer(Character):
    """Archer class inheriting from Character"""
    
    def __init__(self, name, health=120):
        super().__init__(name, health)
        self.arrows = 50
        self.bow = "Wooden Bow"
        self.skills = ["Precision Shot", "Quick Draw"]
        self.accuracy = 85
    
    def attack(self):  # Method overriding
        """Archer's ranged attack"""
        if self.arrows > 0:
            self.arrows -= 1
            damage = 20 + (self.level * 4)
            return f"🏹 {self.name} shoots an arrow for {damage} damage! (Arrows: {self.arrows})"
        return f"❌ {self.name} is out of arrows!"
    
    def precision_shot(self):
        """Special high-accuracy attack"""
        if self.arrows >= 3:
            self.arrows -= 3
            damage = 45 + (self.level * 8)
            return f"🎯 {self.name} uses Precision Shot for {damage} critical damage! (Arrows: {self.arrows})"
        return f"❌ {self.name} needs 3 arrows for Precision Shot!"

# 🌟 Paladin class (Multiple Inheritance - Warrior + Mage abilities)
class Paladin(Warrior, Mage):
    """Paladin class inheriting from both Warrior and Mage"""
    
    def __init__(self, name, health=140):
        # Initialize both parent classes carefully
        Character.__init__(self, name, health)  # Initialize base class once
        self.weapon = "Holy Sword"
        self.armor = "Plate Armor"
        self.mana = 80
        self.max_mana = 80
        self.skills = ["Holy Strike", "Divine Heal", "Blessed Shield"]
        self.faith = 100
    
    def attack(self):  # Override both parent attacks
        """Paladin's holy attack"""
        if self.mana >= 15:
            self.mana -= 15
            damage = 35 + (self.level * 6)
            return f"✨ {self.name} performs Holy Strike for {damage} divine damage! (Mana: {self.mana}/{self.max_mana})"
        # Fall back to warrior attack if no mana
        return super().attack()
    
    def divine_heal(self):
        """Powerful healing ability"""
        if self.mana >= 25:
            self.mana -= 25
            heal_amount = 60 + (self.level * 8)
            return self.heal(heal_amount) + f" (Divine power! Mana: {self.mana}/{self.max_mana})"
        return f"❌ {self.name} needs 25 mana for Divine Heal!"

# 🎮 Interactive Demonstration
print("=== Creating Different Character Types ===")
warrior = Warrior("Conan")
mage = Mage("Gandalf")
archer = Archer("Legolas")
paladin = Paladin("Arthur")

characters = [warrior, mage, archer, paladin]

print("=== Character Stats ===")
for character in characters:
    print(character.display_stats())

print("=== Polymorphism in Action (same method, different behavior) ===")
for character in characters:
    print(character.attack())

print("\n=== Unique Abilities ===")
print(warrior.berserker_rage())
print(mage.cast_heal())
print(archer.precision_shot())
print(paladin.divine_heal())

print("\n=== Method Resolution Order (MRO) for Paladin ===")
print("Paladin MRO:", [cls.__name__ for cls in Paladin.__mro__])
```

### 🔍 Method Resolution Order (MRO):

```
┌─────────────────────────────────────────────────────────────────┐
│                    METHOD RESOLUTION ORDER                      │
├─────────────────────────────────────────────────────────────────┤
│  For multiple inheritance, Python uses C3 linearization:        │
│                                                                 │
│  class Paladin(Warrior, Mage):                                  │
│      pass                                                       │
│                                                                 │
│  MRO: Paladin → Warrior → Mage → Character → object             │
│                                                                 │
│  When calling super(), Python follows this order to find        │
│  the next method in the hierarchy.                              │
└─────────────────────────────────────────────────────────────────┘
```

---

## ✨ Special Methods (Dunder Methods)

Special methods (also called "magic methods" or "dunder methods") allow your classes to integrate seamlessly with Python's built-in functions and operators.

### 🎭 Common Special Methods:

```
┌─────────────────────────────────────────────────────────────────┐
│                    SPECIAL METHODS CATEGORIES                   │
├─────────────────┬───────────────────────────────────────────────┤
│ OBJECT CREATION │ __new__, __init__, __del__                    │
│ STRING REPR     │ __str__, __repr__, __format__                 │
│ COMPARISON      │ __eq__, __lt__, __gt__, __le__, __ge__, __ne__│
│ ARITHMETIC      │ __add__, __sub__, __mul__, __div__, __pow__   │
│ CONTAINER       │ __len__, __getitem__, __setitem__, __iter__   │
│ ATTRIBUTE       │ __getattr__, __setattr__, __delattr__         │
│ CALLABLE        │ __call__                                      │
│ CONTEXT MGR     │ __enter__, __exit__                           │
└─────────────────┴───────────────────────────────────────────────┘
```

### 💎 Comprehensive Example - Vector Class:

```python
import math
from functools import total_ordering

@total_ordering  # Decorator that generates comparison methods
class Vector:
    """A 2D vector class demonstrating special methods"""
    
    def __init__(self, x=0, y=0):
        """Initialize vector with x and y components"""
        self.x = x
        self.y = y
    
    # 📝 String Representation
    def __str__(self):
        """Human-readable string representation"""
        return f"Vector({self.x}, {self.y})"
    
    def __repr__(self):
        """Developer-friendly string representation"""
        return f"Vector(x={self.x}, y={self.y})"
    
    # 🔍 Comparison Methods
    def __eq__(self, other):
        """Check if vectors are equal"""
        if not isinstance(other, Vector):
            return NotImplemented
        return self.x == other.x and self.y == other.y
    
    def __lt__(self, other):
        """Compare vectors by magnitude (for @total_ordering)"""
        if not isinstance(other, Vector):
            return NotImplemented
        return self.magnitude() < other.magnitude()
    
    # ➕ Arithmetic Operations
    def __add__(self, other):
        """Add two vectors"""
        if isinstance(other, Vector):
            return Vector(self.x + other.x, self.y + other.y)
        elif isinstance(other, (int, float)):
            return Vector(self.x + other, self.y + other)
        return NotImplemented
    
    def __radd__(self, other):
        """Reverse addition (when vector is on the right)"""
        return self.__add__(other)
    
    def __sub__(self, other):
        """Subtract vectors"""
        if isinstance(other, Vector):
            return Vector(self.x - other.x, self.y - other.y)
        elif isinstance(other, (int, float)):
            return Vector(self.x - other, self.y - other)
        return NotImplemented
    
    def __mul__(self, scalar):
        """Multiply vector by scalar"""
        if isinstance(scalar, (int, float)):
            return Vector(self.x * scalar, self.y * scalar)
        return NotImplemented
    
    def __rmul__(self, scalar):
        """Reverse multiplication (scalar * vector)"""
        return self.__mul__(scalar)
    
    def __truediv__(self, scalar):
        """Divide vector by scalar"""
        if isinstance(scalar, (int, float)) and scalar != 0:
            return Vector(self.x / scalar, self.y / scalar)
        return NotImplemented
    
    def __neg__(self):
        """Negate vector"""
        return Vector(-self.x, -self.y)
    
    def __abs__(self):
        """Absolute value (magnitude)"""
        return self.magnitude()
    
    def __pow__(self, power):
        """Raise vector components to a power"""
        return Vector(self.x ** power, self.y ** power)
    
    # 📏 Container-like Methods
    def __len__(self):
        """Return number of components (always 2 for 2D vector)"""
        return 2
    
    def __getitem__(self, index):
        """Allow indexing: vector[0] = x, vector[1] = y"""
        if index == 0:
            return self.x
        elif index == 1:
            return self.y
        else:
            raise IndexError("Vector index out of range")
    
    def __setitem__(self, index, value):
        """Allow item assignment: vector[0] = 5"""
        if index == 0:
            self.x = value
        elif index == 1:
            self.y = value
        else:
            raise IndexError("Vector index out of range")
    
    def __iter__(self):
        """Make vector iterable"""
        yield self.x
        yield self.y
    
    # 🎯 Callable
    def __call__(self, new_x=None, new_y=None):
        """Make vector callable to update coordinates"""
        if new_x is not None:
            self.x = new_x
        if new_y is not None:
            self.y = new_y
        return self
    
    # 🔢 Numeric Conversion
    def __bool__(self):
        """Check if vector is non-zero"""
        return self.x != 0 or self.y != 0
    
    def __float__(self):
        """Convert to float (magnitude)"""
        return self.magnitude()
    
    def __int__(self):
        """Convert to int (magnitude as integer)"""
        return int(self.magnitude())
    
    # 🧮 Hash Support (for use in sets/dicts)
    def __hash__(self):
        """Make vector hashable"""
        return hash((self.x, self.y))
    
    # 🎨 Custom Methods
    def magnitude(self):
        """Calculate vector magnitude"""
        return math.sqrt(self.x**2 + self.y**2)
    
    def normalize(self):
        """Return normalized vector"""
        mag = self.magnitude()
        if mag == 0:
            return Vector(0, 0)
        return Vector(self.x / mag, self.y / mag)
    
    def dot_product(self, other):
        """Calculate dot product with another vector"""
        return self.x * other.x + self.y * other.y
    
    def angle_with(self, other):
        """Calculate angle between vectors in degrees"""
        dot = self.dot_product(other)
        mags = self.magnitude() * other.magnitude()
        if mags == 0:
            return 0
        cos_angle = dot / mags
        cos_angle = max(-1, min(1, cos_angle))  # Clamp to avoid floating-point errors
        return math.degrees(math.acos(cos_angle))

# 🎮 Interactive Demonstration
print("=== Creating Vectors ===")
v1 = Vector(3, 4)
v2 = Vector(1, 2)
v3 = Vector(3, 4)  # Same as v1

print(f"v1: {v1}")
print(f"v2: {v2}")
print(f"v3: {v3}")

print(f"\n=== String Representations ===")
print(f"str(v1): {str(v1)}")
print(f"repr(v1): {repr(v1)}")

print(f"\n=== Comparison Operations ===")
print(f"v1 == v2: {v1 == v2}")
print(f"v1 == v3: {v1 == v3}")
print(f"v1 < v2: {v1 < v2}")
print(f"v1 > v2: {v1 > v2}")

print(f"\n=== Arithmetic Operations ===")
print(f"v1 + v2: {v1 + v2}")
print(f"v1 - v2: {v1 - v2}")
print(f"v1 * 2: {v1 * 2}")
print(f"3 * v1: {3 * v1}")
print(f"v1 / 2: {v1 / 2}")
print(f"-v1: {-v1}")
print(f"abs(v1): {abs(v1)}")
print(f"v1 ** 2: {v1 ** 2}")

print(f"\n=== Container-like Operations ===")
print(f"len(v1): {len(v1)}")
print(f"v1[0]: {v1[0]}")
print(f"v1[1]: {v1[1]}")

# Modify using indexing
v1[0] = 5
print(f"After v1[0] = 5: {v1}")

print(f"\n=== Iteration ===")
print("Components of v1:")
for component in v1:
    print(f"  {component}")

print(f"\n=== Boolean and Numeric Conversion ===")
zero_vector = Vector(0, 0)
print(f"bool(v1): {bool(v1)}")
print(f"bool(zero_vector): {bool(zero_vector)}")
print(f"float(v1): {float(v1)}")
print(f"int(v1): {int(v1)}")

print(f"\n=== Callable Behavior ===")
print(f"Before: {v1}")
v1(10, 20)  # Call vector to update coordinates
print(f"After v1(10, 20): {v1}")

print(f"\n=== Vector Mathematics ===")
v1 = Vector(3, 4)
v2 = Vector(1, 2)
print(f"v1 magnitude: {v1.magnitude():.2f}")
print(f"v1 normalized: {v1.normalize()}")
print(f"v1 · v2 (dot product): {v1.dot_product(v2)}")
print(f"Angle between v1 and v2: {v1.angle_with(v2):.2f}°")

print(f"\n=== Hash Support (for sets/dicts) ===")
vector_set = {Vector(1, 2), Vector(3, 4), Vector(1, 2)}
print(f"Vector set: {vector_set}")  # Duplicates removed
```

### 🎯 Special Methods Usage Guide:

```
┌───────────────────────────────────────────────────────────────┐
│                    WHEN TO IMPLEMENT                          │
├─────────────────┬─────────────────────────────────────────────┤
│ __str__         │ Always - for user-friendly string repr      │
│ __repr__        │ Always - for debugging and development      │
│ __eq__          │ If objects can be compared for equality     │
│ __hash__        │ If objects will be used in sets/dict keys   │
│ __bool__        │ If objects have a "truthiness" concept      │
│ __len__         │ If objects have a size/length concept       │
│ __getitem__     │ If objects should support indexing          │
│ __iter__        │ If objects should be iterable               │
│ __call__        │ If objects should act like functions        │
│ __add__, etc.   │ If objects support arithmetic operations    │
└─────────────────┴─────────────────────────────────────────────┘
```

---

## 🎛️ Properties & Decorators

Properties provide a way to use methods as attributes, allowing you to add validation and control access without changing the interface.

### 🎭 Property Decorator Pattern:

```python
class Temperature:
    """A class demonstrating properties and validation"""
    
    def __init__(self, celsius=0):
        self._celsius = 0  # Private attribute
        self.celsius = celsius  # Use property setter for validation
    
    @property
    def celsius(self):
        """Getter for celsius temperature"""
        return self._celsius
    
    @celsius.setter
    def celsius(self, value):
        """Setter with validation for celsius temperature"""
        if not isinstance(value, (int, float)):
            raise TypeError("Temperature must be a number")
        if value < -273.15:
            raise ValueError("Temperature cannot be below absolute zero (-273.15°C)")
        self._celsius = value
    
    @celsius.deleter
    def celsius(self):
        """Deleter for celsius temperature"""
        print("Deleting temperature value")
        self._celsius = 0
    
    @property
    def fahrenheit(self):
        """Computed property for fahrenheit"""
        return (self._celsius * 9/5) + 32
    
    @fahrenheit.setter
    def fahrenheit(self, value):
        """Set temperature using fahrenheit"""
        if not isinstance(value, (int, float)):
            raise TypeError("Temperature must be a number")
        celsius_value = (value - 32) * 5/9
        self.celsius = celsius_value  # Use celsius setter for validation
    
    @property
    def kelvin(self):
        """Computed property for kelvin"""
        return self._celsius + 273.15
    
    @kelvin.setter
    def kelvin(self, value):
        """Set temperature using kelvin"""
        if not isinstance(value, (int, float)):
            raise TypeError("Temperature must be a number")
        celsius_value = value - 273.15
        self.celsius = celsius_value  # Use celsius setter for validation
    
    def __str__(self):
        return f"{self._celsius:.1f}°C / {self.fahrenheit:.1f}°F / {self.kelvin:.1f}K"

# 🎮 Property Demonstration
print("=== Creating Temperature Object ===")
temp = Temperature(25)
print(f"Initial temperature: {temp}")

print(f"\n=== Using Properties Like Attributes ===")
print(f"Celsius: {temp.celsius}")
print(f"Fahrenheit: {temp.fahrenheit}")
print(f"Kelvin: {temp.kelvin}")

print(f"\n=== Setting Temperature Using Different Scales ===")
temp.fahrenheit = 100
print(f"After setting fahrenheit to 100: {temp}")

temp.kelvin = 300
print(f"After setting kelvin to 300: {temp}")

print(f"\n=== Validation in Action ===")
try:
    temp.celsius = -300  # Below absolute zero
except ValueError as e:
    print(f"❌ Error: {e}")

try:
    temp.celsius = "hot"  # Wrong type
except TypeError as e:
    print(f"❌ Error: {e}")
```

### 🏪 Advanced Example - Smart Shopping Cart:

```python
from datetime import datetime, timedelta
from typing import List, Dict

class Product:
    """Simple product class"""
    def __init__(self, name: str, price: float, category: str = "General"):
        self.name = name
        self.price = price
        self.category = category
    
    def __str__(self):
        return f"{self.name} - ${self.price:.2f}"

class ShoppingCart:
    """Advanced shopping cart with properties and validation"""
    
    def __init__(self, customer_name: str, max_items: int = 50):
        self._customer_name = customer_name
        self._items: List[Product] = []
        self._max_items = max_items
        self._discount_rate = 0.0
        self._tax_rate = 0.08
        self._created_at = datetime.now()
    
    # 👤 Customer Properties
    @property
    def customer_name(self):
        """Get customer name"""
        return self._customer_name
    
    @customer_name.setter
    def customer_name(self, name: str):
        """Set customer name with validation"""
        if not isinstance(name, str):
            raise TypeError("Customer name must be a string")
        if len(name.strip()) < 2:
            raise ValueError("Customer name must be at least 2 characters")
        self._customer_name = name.strip().title()
    
    # 🛒 Cart Capacity Properties
    @property
    def max_items(self):
        """Get maximum items allowed"""
        return self._max_items
    
    @max_items.setter
    def max_items(self, value: int):
        """Set maximum items with validation"""
        if not isinstance(value, int):
            raise TypeError("Max items must be an integer")
        if value < 1:
            raise ValueError("Max items must be positive")
        if len(self._items) > value:
            raise ValueError(f"Cart has {len(self._items)} items, cannot set max to {value}")
        self._max_items = value
    
    # 💰 Discount Properties
    @property
    def discount_rate(self):
        """Get discount rate as percentage"""
        return self._discount_rate * 100
    
    @discount_rate.setter
    def discount_rate(self, percentage: float):
        """Set discount rate (0-100)"""
        if not isinstance(percentage, (int, float)):
            raise TypeError("Discount rate must be a number")
        if not 0 <= percentage <= 100:
            raise ValueError("Discount rate must be between 0 and 100")
        self._discount_rate = percentage / 100
    
    # 📊 Read-only Computed Properties
    @property
    def item_count(self) -> int:
        """Get number of items in cart (read-only)"""
        return len(self._items)
    
    @property
    def subtotal(self) -> float:
        """Calculate subtotal before discount and tax (read-only)"""
        return sum(item.price for item in self._items)
    
    @property
    def discount_amount(self) -> float:
        """Calculate discount amount (read-only)"""
        return self.subtotal * self._discount_rate
    
    @property
    def discounted_total(self) -> float:
        """Calculate total after discount (read-only)"""
        return self.subtotal - self.discount_amount
    
    @property
    def tax_amount(self) -> float:
        """Calculate tax amount (read-only)"""
        return self.discounted_total * self._tax_rate
    
    @property
    def total(self) -> float:
        """Calculate final total (read-only)"""
        return self.discounted_total + self.tax_amount
    
    @property
    def categories(self) -> Dict[str, int]:
        """Get item count by category (read-only)"""
        categories = {}
        for item in self._items:
            categories[item.category] = categories.get(item.category, 0) + 1
        return categories
    
    @property
    def is_empty(self) -> bool:
        """Check if cart is empty (read-only)"""
        return len(self._items) == 0
    
    @property
    def is_full(self) -> bool:
        """Check if cart is full (read-only)"""
        return len(self._items) >= self._max_items
    
    @property
    def age_minutes(self) -> float:
        """Get cart age in minutes (read-only)"""
        return (datetime.now() - self._created_at).total_seconds() / 60
    
    # 🛠️ Cart Operations
    def add_item(self, product: Product):
        """Add item to cart"""
        if self.is_full:
            raise ValueError(f"Cart is full (max {self._max_items} items)")
        self._items.append(product)
        return f"✅ Added {product.name} to cart"
    
    def remove_item(self, product_name: str):
        """Remove item from cart by name"""
        for i, item in enumerate(self._items):
            if item.name.lower() == product_name.lower():
                removed = self._items.pop(i)
                return f"🗑️ Removed {removed.name} from cart"
        raise ValueError(f"Product '{product_name}' not found in cart")
    
    def clear(self):
        """Clear all items from cart"""
        count = len(self._items)
        self._items.clear()
        return f"🧹 Cleared {count} items from cart"
    
    def get_summary(self):
        """Get cart summary"""
        if self.is_empty:
            return "🛒 Cart is empty"
        
        summary = f"""
        🛒 Shopping Cart Summary for {self.customer_name}
        ├─ Items: {self.item_count}/{self.max_items}
        ├─ Categories: {', '.join(f'{cat}({count})' for cat, count in self.categories.items())}
        ├─ Subtotal: ${self.subtotal:.2f}
        ├─ Discount ({self.discount_rate:.1f}%): -${self.discount_amount:.2f}
        ├─ After Discount: ${self.discounted_total:.2f}
        ├─ Tax ({self._tax_rate*100:.1f}%): ${self.tax_amount:.2f}
        ├─ Total: ${self.total:.2f}
        └─ Cart Age: {self.age_minutes:.1f} minutes
        
        Items:
        """
        
        for i, item in enumerate(self._items, 1):
            summary += f"  {i}. {item}\n"
        
        return summary

# 🎮 Advanced Properties Demo
print("=== Creating Smart Shopping Cart ===")
cart = ShoppingCart("john doe")
print(f"Customer: {cart.customer_name}")  # Auto-formatted

# Add products
products = [
    Product("Laptop", 999.99, "Electronics"),
    Product("Mouse", 29.99, "Electronics"),
    Product("Coffee", 12.99, "Food"),
    Product("Book", 19.99, "Education")
]

for product in products:
    print(cart.add_item(product))

print(f"\n=== Using Read-only Properties ===")
print(f"Item count: {cart.item_count}")
print(f"Is empty: {cart.is_empty}")
print(f"Is full: {cart.is_full}")
print(f"Categories: {cart.categories}")

print(f"\n=== Using Writable Properties ===")
cart.discount_rate = 10  # 10% discount
print(f"Discount rate: {cart.discount_rate}%")

cart.max_items = 100
print(f"Max items updated to: {cart.max_items}")

print(f"\n=== Property Validation ===")
try:
    cart.discount_rate = 150  # Invalid discount
except ValueError as e:
    print(f"❌ Error: {e}")

try:
    cart.customer_name = "A"  # Too short
except ValueError as e:
    print(f"❌ Error: {e}")

print(cart.get_summary())
```

### 🎛️ Property vs Method Decision Guide:

```
┌───────────────────────────────────────────────────────────────┐
│                  PROPERTY vs METHOD GUIDE                     │
├─────────────────┬─────────────────────────────────────────────┤
│ USE PROPERTY    │ • Represents an attribute/characteristic    │
│                 │ • Quick calculation (no heavy computation)  │
│                 │ • No side effects                           │
│                 │ • Feels like data access                    │
│                 │ • Examples: age, temperature, total         │
├─────────────────┼─────────────────────────────────────────────┤
│ USE METHOD      │ • Represents an action/operation            │
│                 │ • Heavy computation or I/O operations       │
│                 │ • Has side effects                          │
│                 │ • Requires parameters                       │
│                 │ • Examples: save(), calculate(), send()     │
└─────────────────┴─────────────────────────────────────────────┘
```

---

## 🔬 Advanced Topics

### 🎭 Metaclasses - Classes that Create Classes

```python
class SingletonMeta(type):
    """Metaclass that implements Singleton pattern"""
    _instances = {}
    
    def __call__(cls, *args, **kwargs):
        if cls not in cls._instances:
            instance = super().__call__(*args, **kwargs)
            cls._instances[cls] = instance
        return cls._instances[cls]

class DatabaseConnection(metaclass=SingletonMeta):
    """Database connection using Singleton pattern"""
    
    def __init__(self, host="localhost"):
        self.host = host
        self.connected = False
        print(f"🔌 Creating database connection to {host}")
    
    def connect(self):
        self.connected = True
        return f"✅ Connected to {self.host}"

# Demo: Only one instance is created
db1 = DatabaseConnection("server1")
db2 = DatabaseConnection("server2")  # Same instance!
print(f"Same instance? {db1 is db2}")  # True
```

### 🎨 Context Managers

```python
class FileManager:
    """Custom context manager for file operations"""
    
    def __init__(self, filename, mode):
        self.filename = filename
        self.mode = mode
        self.file = None
    
    def __enter__(self):
        print(f"📂 Opening file: {self.filename}")
        self.file = open(self.filename, self.mode)
        return self.file
    
    def __exit__(self, exc_type, exc_value, traceback):
        print(f"📁 Closing file: {self.filename}")
        if self.file:
            self.file.close()
        if exc_type:
            print(f"❌ Exception occurred: {exc_type.__name__}: {exc_value}")
        return False  # Don't suppress exceptions

# Usage
with FileManager("example.txt", "w") as f:
    f.write("Hello, World!")
```

---

## 🚀 Real-World Projects

### 🏪 E-Commerce System

```python
from datetime import datetime
from enum import Enum
from typing import List, Optional
import uuid

class OrderStatus(Enum):
    PENDING = "pending"
    CONFIRMED = "confirmed"
    SHIPPED = "shipped"
    DELIVERED = "delivered"
    CANCELLED = "cancelled"

class User:
    """User account management"""
    
    def __init__(self, username: str, email: str, full_name: str):
        self.user_id = str(uuid.uuid4())[:8]
        self.username = username
        self.email = email
        self.full_name = full_name
        self.created_at = datetime.now()
        self.is_active = True
    
    def __str__(self):
        return f"User({self.username}, {self.email})"

class Product:
    """Product catalog management"""
    
    def __init__(self, name: str, price: float, description: str, stock: int):
        self.product_id = str(uuid.uuid4())[:8]
        self.name = name
        self.price = price
        self.description = description
        self.stock = stock
        self.created_at = datetime.now()
    
    @property
    def is_available(self) -> bool:
        return self.stock > 0
    
    def reduce_stock(self, quantity: int):
        if quantity > self.stock:
            raise ValueError("Insufficient stock")
        self.stock -= quantity
    
    def __str__(self):
        return f"{self.name} - ${self.price:.2f} (Stock: {self.stock})"

class OrderItem:
    """Individual item in an order"""
    
    def __init__(self, product: Product, quantity: int):
        if quantity <= 0:
            raise ValueError("Quantity must be positive")
        if quantity > product.stock:
            raise ValueError("Insufficient stock")
        
        self.product = product
        self.quantity = quantity
        self.unit_price = product.price
    
    @property
    def total_price(self) -> float:
        return self.unit_price * self.quantity
    
    def __str__(self):
        return f"{self.quantity}x {self.product.name} @ ${self.unit_price:.2f}"

class Order:
    """Order management system"""
    
    def __init__(self, user: User):
        self.order_id = str(uuid.uuid4())[:8]
        self.user = user
        self.items: List[OrderItem] = []
        self.status = OrderStatus.PENDING
        self.created_at = datetime.now()
        self.updated_at = datetime.now()
    
    def add_item(self, product: Product, quantity: int):
        """Add item to order"""
        if self.status != OrderStatus.PENDING:
            raise ValueError("Cannot modify confirmed order")
        
        # Check if product already in order
        for item in self.items:
            if item.product.product_id == product.product_id:
                item.quantity += quantity
                return
        
        # Add new item
        order_item = OrderItem(product, quantity)
        self.items.append(order_item)
        self.updated_at = datetime.now()
    
    @property
    def total_amount(self) -> float:
        return sum(item.total_price for item in self.items)
    
    @property
    def total_items(self) -> int:
        return sum(item.quantity for item in self.items)
    
    def confirm_order(self):
        """Confirm order and reduce stock"""
        if self.status != OrderStatus.PENDING:
            raise ValueError("Order already confirmed")
        
        if not self.items:
            raise ValueError("Cannot confirm empty order")
        
        # Reduce stock for all items
        for item in self.items:
            item.product.reduce_stock(item.quantity)
        
        self.status = OrderStatus.CONFIRMED
        self.updated_at = datetime.now()
    
    def cancel_order(self):
        """Cancel order and restore stock"""
        if self.status in [OrderStatus.SHIPPED, OrderStatus.DELIVERED]:
            raise ValueError("Cannot cancel shipped/delivered order")
        
        if self.status == OrderStatus.CONFIRMED:
            # Restore stock
            for item in self.items:
                item.product.stock += item.quantity
        
        self.status = OrderStatus.CANCELLED
        self.updated_at = datetime.now()
    
    def get_summary(self):
        """Get order summary"""
        summary = f"""
        📦 Order #{self.order_id}
        ├─ Customer: {self.user.full_name}
        ├─ Status: {self.status.value.title()}
        ├─ Items: {self.total_items}
        ├─ Total: ${self.total_amount:.2f}
        ├─ Created: {self.created_at.strftime('%Y-%m-%d %H:%M')}
        └─ Updated: {self.updated_at.strftime('%Y-%m-%d %H:%M')}
        
        Items:
        """
        
        for i, item in enumerate(self.items, 1):
            summary += f"  {i}. {item} = ${item.total_price:.2f}\n"
        
        return summary

class ECommerceSystem:
    """Main e-commerce system"""
    
    def __init__(self):
        self.users: List[User] = []
        self.products: List[Product] = []
        self.orders: List[Order] = []
    
    def register_user(self, username: str, email: str, full_name: str) -> User:
        """Register new user"""
        # Check for duplicate username
        if any(user.username == username for user in self.users):
            raise ValueError("Username already exists")
        
        user = User(username, email, full_name)
        self.users.append(user)
        return user
    
    def add_product(self, name: str, price: float, description: str, stock: int) -> Product:
        """Add product to catalog"""
        product = Product(name, price, description, stock)
        self.products.append(product)
        return product
    
    def create_order(self, user: User) -> Order:
        """Create new order for user"""
        order = Order(user)
        self.orders.append(order)
        return order
    
    def get_user_orders(self, user: User) -> List[Order]:
        """Get all orders for a user"""
        return [order for order in self.orders if order.user.user_id == user.user_id]
    
    def get_system_stats(self):
        """Get system statistics"""
        total_revenue = sum(
            order.total_amount for order in self.orders 
            if order.status in [OrderStatus.CONFIRMED, OrderStatus.SHIPPED, OrderStatus.DELIVERED]
        )
        
        return f"""
        📊 E-Commerce System Statistics
        ├─ Users: {len(self.users)}
        ├─ Products: {len(self.products)}
        ├─ Orders: {len(self.orders)}
        └─ Total Revenue: ${total_revenue:.2f}
        """

# 🎮 E-Commerce Demo
print("=== Setting Up E-Commerce System ===")
ecommerce = ECommerceSystem()

# Register users
alice = ecommerce.register_user("alice", "alice@email.com", "Alice Johnson")
bob = ecommerce.register_user("bob", "bob@email.com", "Bob Smith")

# Add products
laptop = ecommerce.add_product("Gaming Laptop", 1299.99, "High-performance gaming laptop", 10)
mouse = ecommerce.add_product("Gaming Mouse", 79.99, "RGB gaming mouse", 25)
keyboard = ecommerce.add_product("Mechanical Keyboard", 149.99, "Cherry MX switches", 15)

print(f"\n=== Products Available ===")
for product in ecommerce.products:
    print(f"  {product}")

# Create orders
print(f"\n=== Creating Orders ===")
order1 = ecommerce.create_order(alice)
order1.add_item(laptop, 1)
order1.add_item(mouse, 2)

order2 = ecommerce.create_order(bob)
order2.add_item(keyboard, 1)
order2.add_item(mouse, 1)

print(order1.get_summary())
print(order2.get_summary())

# Confirm orders
print("=== Confirming Orders ===")
order1.confirm_order()
order2.confirm_order()

print(f"Updated stock levels:")
for product in ecommerce.products:
    print(f"  {product}")

print(ecommerce.get_system_stats())
```

---

## 💡 Best Practices

### ✅ Do's and Don'ts

```python
# ✅ GOOD PRACTICES

class GoodBankAccount:
    """Well-designed bank account class following best practices"""
    
    def __init__(self, account_holder: str, initial_balance: float = 0):
        # Use descriptive names
        self.account_holder = account_holder
        self._balance = initial_balance  # Protected for internal use
        self._transaction_history = []
        
        # Validate input
        if initial_balance < 0:
            raise ValueError("Initial balance cannot be negative")
    
    @property
    def balance(self) -> float:
        """Get current balance (read-only property)"""
        return self._balance
    
    def deposit(self, amount: float) -> str:
        """Deposit money into account"""
        if amount <= 0:
            raise ValueError("Deposit amount must be positive")
        
        self._balance += amount
        self._log_transaction("DEPOSIT", amount)
        return f"Deposited ${amount:.2f}. New balance: ${self._balance:.2f}"
    
    def _log_transaction(self, transaction_type: str, amount: float):
        """Private method for logging transactions"""
        self._transaction_history.append({
            'type': transaction_type,
            'amount': amount,
            'timestamp': datetime.now()
        })
    
    def __str__(self) -> str:
        """Meaningful string representation"""
        return f"BankAccount(holder={self.account_holder}, balance=${self._balance:.2f})"
    
    def __repr__(self) -> str:
        """Developer-friendly representation"""
        return f"BankAccount({self.account_holder!r}, {self._balance})"


# ❌ BAD PRACTICES

class BadBankAccount:
    """Poorly designed class with common mistakes"""
    
    def __init__(self, n, b=0):  # ❌ Unclear parameter names
        self.n = n  # ❌ Non-descriptive attribute names
        self.b = b  # ❌ No validation
        self.h = []  # ❌ What is 'h'?
    
    def d(self, a):  # ❌ Method names not descriptive
        self.b += a  # ❌ No validation
        return self.b  # ❌ Inconsistent return types
    
    def w(self, a):  # ❌ What does 'w' do?
        if a > self.b:  # ❌ No error handling
            print("Not enough money")  # ❌ Print instead of exception
            return
        self.b -= a
    
    # ❌ No __str__ or __repr__ methods
    # ❌ Direct attribute access without protection
    # ❌ No documentation
```

### 🎯 Class Design Principles:

```
┌─────────────────────────────────────────────────────────────────┐
│                      SOLID PRINCIPLES                           │
├─────────────────────────────────────────────────────────────────┤
│ S - Single Responsibility: One class, one purpose               │
│ O - Open/Closed: Open for extension, closed for modification    │
│ L - Liskov Substitution: Subclasses must be substitutable       │
│ I - Interface Segregation: Many specific interfaces             │
│ D - Dependency Inversion: Depend on abstractions                │
└─────────────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────────────┐
│                    NAMING CONVENTIONS                           │
├─────────────────────────────────────────────────────────────────┤
│ Classes:          PascalCase (MyClass, BankAccount)             │
│ Methods/Vars:     snake_case (get_balance, user_name)           │
│ Constants:        UPPER_SNAKE_CASE (MAX_BALANCE, PI)            │
│ Private:          _single_underscore (_internal_method)         │
│ Name Mangling:    __double_underscore (__private_var)           │
└─────────────────────────────────────────────────────────────────┘
```

---

## 📝 Practice Exercises

### 🎯 Exercise 1: Library Management System

```python
"""
Create a Library Management System with the following requirements:

1. Book class with title, author, ISBN, and availability status
2. Member class with name, member_id, and borrowed books list
3. Library class that manages books and members
4. Implement borrowing and returning functionality
5. Add search functionality for books
6. Track overdue books with due dates

Bonus: Add different member types (Student, Faculty) with different borrowing limits
"""

# Your solution here
class Book:
    pass

class Member:
    pass

class Library:
    pass
```

### 🎯 Exercise 2: Vehicle Rental System

```python
"""
Design a Vehicle Rental System:

1. Create a base Vehicle class
2. Inherit specific vehicle types (Car, Motorcycle, Truck)
3. Implement rental pricing based on vehicle type and duration
4. Add customer management
5. Track rental history
6. Implement vehicle maintenance scheduling

Requirements:
- Use inheritance and polymorphism
- Implement proper encapsulation
- Use properties for calculated values
- Add validation and error handling
"""

# Your solution here
```

### 🎯 Exercise 3: Social Media Platform

```python
"""
Build a simplified social media platform:

1. User class with profile information
2. Post class with content, likes, comments
3. Comment class for post comments
4. Friend system (add/remove friends)
5. News feed functionality
6. Privacy settings

Features to implement:
- User authentication simulation
- Post visibility based on privacy settings
- Like and comment functionality
- Friend recommendations
- Post search and filtering
"""

# Your solution here
```

---

## 🎓 Conclusion

Congratulations! You've mastered Python classes and Object-Oriented Programming. Here's what you've learned:

```
🎯 KEY TAKEAWAYS
├─ 🏗️ Class Structure: Attributes, methods, constructors
├─ 🔧 Instance vs Class Variables: Understanding scope
├─ 📦 Method Types: Instance, class, and static methods
├─ 🔒 Encapsulation: Public, protected, and private members
├─ 🌳 Inheritance: Code reuse and hierarchical relationships
├─ ✨ Special Methods: Integration with Python's built-ins
├─ 🎛️ Properties: Controlled attribute access
├─ 🔬 Advanced Topics: Metaclasses and context managers
├─ 🚀 Real Projects: Practical applications
└─ 💡 Best Practices: Clean, maintainable code
```

### 🚀 Next Steps:

1. **Practice**: Build your own projects using these concepts
2. **Explore**: Learn about design patterns (Singleton, Factory, Observer)
3. **Advanced**: Study metaclasses, descriptors, and decorators in depth
4. **Frameworks**: Apply OOP knowledge to Django, Flask, or other frameworks
5. **Testing**: Learn to write unit tests for your classes

### 📚 Additional Resources:

- [Python Official Documentation](https://docs.python.org/3/tutorial/classes.html)
- [Real Python OOP Tutorials](https://realpython.com/python3-object-oriented-programming/)
- [Corey Schafer's OOP Series](https://www.youtube.com/playlist?list=PL-osiE80TeTsqhIuOqKhwlXsIBIdSeYtc)

---

```
🎉 Happy Coding! 🐍
Remember: "Code is read much more often than it is written"
Write clear, maintainable, and well-documented classes!

             ╭─────────────────╮
             │   PYTHON OOP    │
             │    MASTERED!    │
             ╰─────────────────╯
                      🎓
```

---

*Created with ❤️ for Python learners everywhere*