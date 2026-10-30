# Polymorphism

## Overview

Polymorphism is one of the most important concepts in Object-Oriented Programming (OOP). The word polymorphism comes from two Greek words: "poly" meaning many, and "morph" meaning forms. In programming, polymorphism means that one method, operator, or object can behave differently depending on the situation.

## Learning Objectives

- Understand the concept of polymorphism
- Learn different types of polymorphism in Python
- Apply method overloading, overriding, and operator overloading
- Understand duck typing in Python

## What I Learned

### Concept of Polymorphism

Polymorphism allows the same action to produce different results. This makes programs more flexible, reusable, and easier to maintain.

Real-world example: A person can be a student in school, an employee at work, and a customer in a store. Even though it is the same person, the behavior changes depending on the situation.

### Importance of Polymorphism

- Reduces code duplication
- Makes programs more flexible
- Improves code readability
- Allows one interface to be used for different data types
- Makes programs easier to maintain and expand

## Types of Polymorphism

### 1. Method Overloading

Method overloading is the ability of a method to perform different tasks depending on the number or type of arguments passed to it.

Python handles method overloading differently because it does not support traditional method overloading directly. Instead, Python achieves similar behavior using default arguments or variable-length arguments.

**Example:**

```python
class Calculator:
    def add(self, a, b, c=0):
        return a + b + c

calc = Calculator()
print(calc.add(2, 3))      # Output: 5
print(calc.add(2, 3, 4))   # Output: 9
```

**Advantages:**
- Improves code readability
- Reduces the need for multiple method names
- Makes programs more flexible

### 2. Method Overriding

Method overriding happens when a child class provides its own version of a method that already exists in the parent class. The child class replaces or modifies the behavior of the inherited method.

**Example:**

```python
class Animal:
    def sound(self):
        print("Animals make sounds")

class Dog(Animal):
    def sound(self):
        print("Dog barks")

dog = Dog()
dog.sound()  # Output: Dog barks
```

**Advantages:**
- Allows customization of inherited methods
- Improves flexibility
- Supports runtime polymorphism

### 3. Operator Overloading

Operator overloading means giving additional meaning or behavior to operators depending on the objects used. Python allows operators like +, -, *, /, == to work differently for different data types.

**Example:**

```python
print(5 + 3)           # Output: 8
print("Hello " + "World")  # Output: Hello World
```

**Custom Operator Overloading Example:**

```python
class Box:
    def __init__(self, value):
        self.value = value
    
    def __add__(self, other):
        return self.value + other.value

b1 = Box(10)
b2 = Box(20)
print(b1 + b2)  # Output: 30
```

**Advantages:**
- Makes code more readable
- Allows custom object behavior
- Improves flexibility

### 4. Duck Typing

Duck typing is a concept in Python where the type of an object is less important than the methods or behaviors it has. Python focuses on "What an object can do" instead of "What type the object is."

**Example:**

```python
class Dog:
    def speak(self):
        print("Woof")

class Cat:
    def speak(self):
        print("Meow")

def animal_sound(animal):
    animal.speak()

d = Dog()
c = Cat()

animal_sound(d)  # Output: Woof
animal_sound(c)  # Output: Meow
```

**Advantages:**
- Makes Python flexible
- Reduces strict type checking
- Encourages reusable code

## Real-World Applications

Polymorphism is widely used in:
- Game development
- Web applications
- Mobile apps
- AI systems
- Banking systems

It allows developers to write cleaner code, reusable programs, scalable systems, and flexible applications.

## Key Takeaways

- Polymorphism allows the same action to produce different results
- Python achieves method overloading through default arguments
- Method overriding lets child classes customize inherited behavior
- Operator overloading gives custom meaning to operators
- Duck typing focuses on object behavior rather than type
- Polymorphism improves code flexibility, reusability, and maintainability
