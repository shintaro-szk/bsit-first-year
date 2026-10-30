# Abstraction in Object-Oriented Programming (OOP)

## Overview

Abstraction is one of the four main principles of Object-Oriented Programming together with Encapsulation, Inheritance, and Polymorphism. It focuses on hiding unnecessary implementation details and showing only the essential features of an object.

In Python, abstraction helps programmers create cleaner, more organized, and reusable code by defining what an object should do rather than how it does it internally.

## Learning Objectives

- Understand the concept of abstraction in OOP
- Learn about abstract classes and abstract methods
- Use the ABC module in Python
- Apply abstraction in real-world scenarios

## What I Learned

### Concept of Abstraction in OOP

Abstraction is the process of hiding complex implementation details and exposing only the necessary functionalities of an object. It allows programmers to focus on what an object does instead of how it works internally.

### Real-World Example: ATM Machine

When using an ATM:
- Users insert a card
- Enter a PIN
- Withdraw money

The user does not see:
- Database verification
- Network communication
- Security algorithms

The complex internal processes are hidden. Only the essential operations are visible. This is abstraction.

### Importance of Abstraction

- **Reduces Complexity**: Hides complex details behind simple interfaces
- **Improves Security**: Internal implementation is protected
- **Enhances Code Reusability**: Common behaviors can be shared
- **Simplifies Maintenance**: Changes to implementation do not affect interface
- **Supports Large-Scale Development**: Essential for complex systems

### Abstraction in Game Development

In games:
- Characters can "attack"
- Vehicles can "move"
- Weapons can "reload"

The game engine only requires these actions to exist, regardless of how they are implemented.

Example: A sword attacks differently from a gun, but both still use an `attack()` method. This demonstrates abstraction.

## Abstract Classes

An abstract class is a class that cannot be instantiated directly. It serves as a blueprint for other classes.

Abstract classes contain:
- Abstract methods
- Shared attributes
- Common behaviors

Subclasses inherit and complete the missing functionality.

### Purpose of Abstract Classes

Abstract classes are used when:
- Multiple classes share common behaviors
- A standard structure is required
- Certain methods must be implemented by subclasses

### Example Scenario: Vehicle System

All vehicles:
- Start
- Stop
- Move

But each vehicle performs these differently. An abstract class ensures every vehicle class includes these methods.

## Abstract Methods

An abstract method is a method declared in an abstract class but has no implementation. Subclasses are required to override and implement it.

### Why Use Abstract Methods?

They enforce consistency among subclasses. If a subclass does not implement all abstract methods:
- Python raises an error
- The subclass cannot be instantiated

### Implementing Abstract Methods

```python
from abc import ABC, abstractmethod

class Animal(ABC):
    @abstractmethod
    def sound(self):
        pass

class Dog(Animal):
    def sound(self):
        return "Woof!"

class Cat(Animal):
    def sound(self):
        return "Meow!"

dog = Dog()
cat = Cat()
print(dog.sound())  # Output: Woof!
print(cat.sound())  # Output: Meow!
```

## The ABC Module in Python

The abc module stands for Abstract Base Classes. It allows Python programmers to create abstract classes and abstract methods.

### Important Components

| Component | Description |
|-----------|-------------|
| ABC | Used to create abstract classes |
| abstractmethod | Decorator for abstract methods |

### Complete Example: Shape Calculator

```python
from abc import ABC, abstractmethod

class Shape(ABC):
    @abstractmethod
    def area(self):
        pass

class Rectangle(Shape):
    def __init__(self, length, width):
        self.length = length
        self.width = width
    
    def area(self):
        return self.length * self.width

class Circle(Shape):
    def __init__(self, radius):
        self.radius = radius
    
    def area(self):
        return 3.14 * self.radius * self.radius

rectangle = Rectangle(5, 4)
circle = Circle(3)
print("Rectangle Area:", rectangle.area())  # Output: 20
print("Circle Area:", circle.area())        # Output: 28.26
```

## Key Rules in Abstraction

| Rule | Explanation |
|------|-------------|
| Abstract classes cannot be instantiated | They only serve as blueprints |
| Subclasses must implement abstract methods | Required for object creation |
| Abstract methods contain no implementation | Only method declarations |
| Abstract classes may contain regular methods | Shared functionality is allowed |

## Difference Between Abstraction and Encapsulation

| Abstraction | Encapsulation |
|-------------|---------------|
| Hides implementation complexity | Hides data |
| Focuses on "what" an object does | Focuses on "how" data is protected |
| Uses abstract classes and methods | Uses private/protected attributes |

## Advantages of Abstraction

- Cleaner code structure
- Easier debugging
- Better scalability
- Improved collaboration among developers
- More maintainable systems
- Encourages modular programming

## Disadvantages of Abstraction

- Can increase program complexity for beginners
- Requires additional planning
- Too much abstraction may make debugging difficult

## Applications in Real Systems

| System | Example of Abstraction |
|---------|----------------------|
| Banking App | Deposit, withdraw, transfer |
| Online Shopping | Checkout process |
| Mobile Apps | Login authentication |
| Video Games | Character movement and attacks |
| School Systems | Student registration |

## Activity: Designing an Abstract Character System

### Activity Scenario

Your game currently contains playable characters, enemies, weapons, or abilities. To improve code organization and scalability, you will redesign part of your game using abstraction.

You must create an abstract base class that defines common actions shared by all game characters. Each subclass must implement its own unique behavior.

### Part 1 – Create an Abstract Class

Using Python's abc module, create an abstract class named `CHARACTER`.

The abstract class must contain:

**Attributes:**
- name
- health

**Abstract Methods:**
- attack()
- special_skill()

### Part 2 – Create Subclasses

Create at least THREE subclasses related to your game.

Examples:
- Warrior
- Mage
- Archer

Each subclass must:
- Inherit from Character
- Override all abstract methods
- Display unique attacks and skills

### Part 3 – Demonstrate Output

Instantiate each subclass and display their actions.

**Example:**
```
Archer attacks using Bow Shot!
Archer uses Arrow Rain!

Mage attacks using Magic Bolt!
Mage casts Meteor Storm!
```

## Key Takeaways

- Abstraction hides implementation details and shows essential features
- Abstract classes cannot be instantiated directly
- Abstract methods must be implemented by subclasses
- The ABC module provides tools for creating abstract classes
- Abstraction improves code organization and scalability
- Abstraction is essential for large-scale development
