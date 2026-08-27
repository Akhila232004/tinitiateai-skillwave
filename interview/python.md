# Python

## What is Python?
Level: Beginner  

### Answer
- Python is a high-level, easy-to-read programming language.
- It is widely used in web development, automation, AI, data science, and scripting.
- Python focuses on simplicity and developer productivity.
- It supports object-oriented, functional, and procedural programming styles.

### Python Code
```python
print("Hello, Python!")
```

---

## What is the difference between a list and a tuple in Python?
Level: Beginner  

### Answer
- A list is mutable, meaning you can change its elements.
- A tuple is immutable, meaning its values cannot be changed after creation.
- Lists use square brackets `[]`.
- Tuples use parentheses `()`.

### Python Code
```python
# List Example
numbers = [1, 2, 3]
numbers.append(4)
print(numbers)

# Tuple Example
colors = ("red", "blue", "green")
print(colors)
```

---

## What is a dictionary in Python?
Level: Beginner  

### Answer
- A dictionary stores data as key-value pairs.
- Keys must be unique.
- Dictionaries are fast for searching values by key.
- They are commonly used for structured data.

### Python Code
```python
student = {
    "name": "Hello",
    "age": 21,
    "course": "Python"
}

print(student["name"])
```

---

## What are functions in Python?
Level: Beginner  

### Answer
- Functions are reusable blocks of code.
- They help organize logic into smaller parts.
- Functions can accept parameters and return values.
- They improve code readability and reusability.

### Python Code
```python
def greet(name):
    return f"Hello, {name}"

message = greet("Hello")
print(message)
```

---

## What is object-oriented programming in Python?
Level: Intermediate  

### Answer
- Python supports object-oriented programming using classes and objects.
- A class is a blueprint for creating objects.
- Objects contain data and methods.
- OOP improves modularity and code reuse.

### Python Code
```python
class Student:
    def __init__(self, name):
        self.name = name

    def introduce(self):
        print(f"My name is {self.name}")

student1 = Student("Hello")
student1.introduce()
```

---

## What is exception handling in Python?
Level: Intermediate  

### Answer
- Exception handling prevents program crashes from runtime errors.
- Python uses `try`, `except`, `finally`, and `raise`.
- It helps create stable and reliable applications.

### Python Code
```python
try:
    number = int(input("Enter a number: "))
    print(number)
except ValueError:
    print("Invalid input")
finally:
    print("Execution completed")
```

---

## What are Python modules?
Level: Beginner  

### Answer
- Modules are files containing reusable Python code.
- They help organize projects into separate files.
- Python provides built-in modules and supports custom modules.

### Python Code
```python
import math

print(math.sqrt(25))
```

---

## What is list comprehension in Python?
Level: Intermediate  

### Answer
- List comprehension provides a short way to create lists.
- It makes code cleaner and more readable.
- It combines loops and conditions in a single line.

### Python Code
```python
squares = [x * x for x in range(5)]

print(squares)
```
