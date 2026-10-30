# Advanced OOP Concepts

## Overview

This topic covers advanced Object-Oriented Programming concepts including composition versus inheritance, and Python magic methods (dunder methods). These concepts enable more flexible, maintainable, and powerful object-oriented designs.

## Learning Objectives

- Understand the difference between composition and inheritance
- Learn when to use composition versus inheritance
- Understand Python magic methods and their purpose
- Implement common magic methods for custom object behavior

## What I Learned

### Composition vs Inheritance

#### Inheritance

Inheritance allows a class to acquire the attributes and methods of another class. It represents an IS-A relationship.

**Examples:**
- A Dog IS an Animal
- A Warrior IS a Character
- A Truck IS a Vehicle

The child class inherits behaviors from the parent class.

**Example:**

```python
class Animal:
    def __init__(self, name):
        self.name = name

class Dog(Animal):
    def bark(self):
        print("Dog is barking")
```

#### Composition

Composition is another OOP technique where one object contains another object as part of its structure. It represents a HAS-A relationship.

**Examples:**
- A Car HAS an Engine
- A Player HAS a Weapon
- A Computer HAS a Keyboard

Instead of inheriting behaviors, objects work together.

**Example:**

```python
class Engine:
    def start(self):
        print("Engine started")

class Car:
    def __init__(self):
        self.engine = Engine()
    
    def drive(self):
        self.engine.start()
        print("Car is moving")
```

**Another Example:**

```python
class HealthSystem:
    def __init__(self, hp):
        self.hp = hp
    
    def take_damage(self, damage):
        self.hp -= damage

class Player:
    def __init__(self, name):
        self.name = name
        self.health = HealthSystem(100)
```

### Comparison: Composition vs Inheritance

| Inheritance | Composition |
|-------------|-------------|
| Represents IS-A relationship | Represents HAS-A relationship |
| Child inherits parent behaviors | Object contains another object |
| Creates tight coupling | More flexible |
| Best for related object types | Best for combining functionalities |

### When to Use Inheritance

Use inheritance when:
- Classes are strongly related
- A subclass is truly a type of the parent
- Shared behavior is necessary

**Examples:**
- Student → Person
- Mage → Character
- Truck → Vehicle

### When to Use Composition

Use composition when:
- Objects need flexible relationships
- Functionality can be separated
- Systems may change frequently

**Examples:**
- Character HAS Weapon
- School HAS Students
- Computer HAS Monitor

### Composition in Game Development

Composition is heavily used in modern game development.

**Example:** A player may contain:
- Weapon
- Inventory
- Armor
- Skills

Instead of inheriting everything, developers create separate objects.

**Benefits:**
- Easier upgrades
- More modular systems
- Better scalability
- Cleaner architecture

## Python Magic Methods

Magic methods are special methods in Python surrounded by double underscores. They are also called dunder methods (double underscore).

**Examples:**
- `__init__()`
- `__str__()`
- `__len__()`

These methods allow objects to interact with built-in Python operations.

### Importance of Magic Methods

Magic methods allow programmers to:
- Customize object behavior
- Make objects more readable
- Integrate objects naturally into Python syntax
- Improve user interaction with classes

Without magic methods, objects may display unreadable outputs.

### Common Magic Methods

#### `__init__()` Method

The `__init__()` method initializes object attributes when an object is created.

**Example:**

```python
class Student:
    def __init__(self, name):
        self.name = name
```

#### `__str__()` Method

The `__str__()` method controls how objects are displayed when printed.

**Without `__str__()`:**
```python
print(object)  # May display: <__main__.Student object at 0x...>
```

**With `__str__()`:**
```python
class Student:
    def __init__(self, name):
        self.name = name
    
    def __str__(self):
        return f"Student Name: {self.name}"

student = Student("John")
print(student)  # Output: Student Name: John
```

#### `__len__()` Method

The `__len__()` method allows objects to work with the `len()` function.

**Example:**

```python
class Team:
    def __init__(self, members):
        self.members = members
    
    def __len__(self):
        return len(self.members)

team = Team(["Alice", "Bob", "Charlie"])
print(len(team))  # Output: 3
```

### Arithmetic Magic Methods

#### `__add__()` – Addition Operator

Allows objects to use the `+` operator.

**Example:**

```python
class Coins:
    def __init__(self, amount):
        self.amount = amount
    
    def __add__(self, other):
        return self.amount + other.amount

c1 = Coins(30)
c2 = Coins(20)
print(c1 + c2)  # Output: 50
```

The `__add__()` method tells Python what should happen when two objects are added using `+`. Without this method, `c1 + c2` would produce an error.

**Useful in:**
- Games
- Banking systems
- Inventory systems
- Point systems

#### `__sub__()` – Subtraction Operator

Allows objects to use the `-` operator. The `__sub__()` method defines how subtraction works for objects.

**Useful in:**
- Health reduction
- Damage systems
- Mana consumption

**Example:**

```python
class Health:
    def __init__(self, hp):
        self.hp = hp
    
    def __sub__(self, damage):
        return self.hp - damage

player = Health(100)
print(player - 30)  # Output: 70
```

#### `__mul__()` – Multiplication Operator

Allows objects to use the `*` operator. The `__mul__()` method defines multiplication behavior.

**Useful for:**
- Critical damage experience
- Multipliers
- Reward systems

**Example:**

```python
class Score:
    def __init__(self, points):
        self.points = points
    
    def __mul__(self, multiplier):
        return self.points * multiplier

score = Score(100)
print(score * 2)  # Output: 200
```

### Comparison Magic Methods

#### `__eq__()` – Equality Comparison

Allows objects to use `==`. The `__eq__()` method compares two objects.

**Useful for:**
- Comparing player levels
- Checking identical items
- Matching scores

**Example:**

```python
class Player:
    def __init__(self, level):
        self.level = level
    
    def __eq__(self, other):
        return self.level == other.level

p1 = Player(10)
p2 = Player(10)
print(p1 == p2)  # Output: True
```

#### `__lt__()` – Less Than Comparison

Allows objects to use `<`. The `__lt__()` method is useful for ranking and sorting.

**Useful for:**
- Ranking systems
- Sorting objects
- Comparing scores

**Example:**

```python
class Score:
    def __init__(self, points):
        self.points = points
    
    def __lt__(self, other):
        return self.points < other.points

s1 = Score(50)
s2 = Score(80)
print(s1 < s2)  # Output: True
```

### Indexing and Membership Magic Methods

#### `__getitem__()` – Index Access

Allows objects to use square brackets `[]`. The `__getitem__()` method allows objects to behave like lists.

**Useful for:**
- Inventories
- Menus
- Data collections

**Example:**

```python
class Inventory:
    def __init__(self, items):
        self.items = items
    
    def __getitem__(self, index):
        return self.items[index]

bag = Inventory(["Sword", "Potion", "Shield"])
print(bag[1])  # Output: Potion
```

#### `__contains__()` – Using the in Keyword

Allows objects to use the `in` keyword for membership testing.

**Example:**

```python
class Inventory:
    def __init__(self, items):
        self.items = items
    
    def __contains__(self, item):
        return item in self.items

bag = Inventory(["Sword", "Potion", "Shield"])
print("Potion" in bag)  # Output: True
print("Bow" in bag)     # Output: False
```

## Key Takeaways

- Inheritance represents IS-A relationships, composition represents HAS-A relationships
- Use inheritance for strongly related classes with shared behavior
- Use composition for flexible, modular designs
- Magic methods (dunder methods) enable custom object behavior
- Magic methods allow objects to interact naturally with Python syntax
- Common magic methods include `__init__`, `__str__`, `__len__`, `__add__`, `__sub__`, `__eq__`, `__lt__`, `__getitem__`, `__contains__`
- Composition is preferred in modern game development for flexibility and scalability
