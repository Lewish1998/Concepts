This is hopefully a helpful yet brief explanation of some concepts I think are important if not essential. I have tried to simplify things and provide examples where I have deemed necessary. Each concept has a link to the relative information.
Enjoy, 

Lewis.

**Contents**:

1. What is OOP? [[#Object Oriented Programming]]
2. What are the 4 pillars of OOP? [[#Four Pillars of OOP]]
3. What is an API and how it is used? [[#API]]
4. What is an algorithm? [[#Algorithm]]
5. What is the difference between an interpreted language and a compiled language? [[#Interpreted/Compiled Languages]]
6. What are operators? [[#Operators]]
7. Name some data types [[#Data Types]]
8. What is a framework/library? [[#Frameworks and Libraries]]
9. What is a CI/CD pipeline? [[#CI/CD Pipelines]]

____________________________________________________________________

# Object Oriented Programming

Object oriented programming is the practice of creating reusable objects which can be used throughout your program. This creates code that is far easier to understand, maintain and expand. OOP encompasses the concepts of classes, inheritance, encapsulation, polymorphism and abstraction.

____________________________________________________________________

# Four Pillars of OOP

The four pillars of OOP are: polymorphism, inheritance, encapsulation and abstraction. An easy way to remember this is PIE-A.

**Polymorphism** allows you to use the same method in different objects. Eg:
```python
class Vehicle:
	def start_engine(self):
	pass

class Car(Vehicle):
	def start_engine(self):
	return "Vroom"

class Plane(Vehicle):
	def start_engine(self):
	return "Woosh"

def engine_sound(vehicle):
	return vehicle.start_engine()
```
In this example, both subclasses inherit from the Vehicle class and therefore are able to use the start_engine() method.
The engine_sound() function takes in a vehicle as a parameter. This function will work for both subclasses due to polymorphism.
The correct start_engine() method is determined at runtime based on the actual object type, allowing for different behaviour baed on the objects class.


**Inheritance** is when a subclass inherits properties and behaviours from its parent class. Eg:
```python
class Employee:
	def __init__(self, name, age):
		self.name = name
		self.age = age

	def greet(self):
		return f"Hi, I'm {self.name} and I'm {self.age} years old."

class Manager(Employee):
	def __init__(self, name, age, manager_id):
		super().__init__(name, age)
		self.manager_id = manager_id

	def greet(self):
		return f"Hi, I'm {self.name} and I'm {self.age} years old. My ID is                {self.manager_id}
```
In this example, the parent class Employee has the attributes name and age, as well as the method greet(). The Manager subclass inherits both name and age from the Employee superclass, as well as the greet() method. The greet() method is then overridden to include the ID.


**Encapsulation** stops certain attributes from being accessed outside of the class, providing more security.
```python
class BankAccount:
	def __init__(self, account_number, balance):
		self.__account_number = account_number
		self.__balance = balance

	def deposit(self, amount):
		if amount > 0:
			self.__balance += amount

	def withdraw(self, amount):
		if 0 < amount <= self.__balance:
			self.__balance -= amount

	def get_balance(self):
		return self.__balance

account1 = BankAccount("1234", 1000)

print(account1.__account_number) # Raises AttributionError
print(account1.__balance) # Raises AttributionError
print(account1.get_balance()) # Outputs balance
account1.__balance = 1000000 # Creates new attribute called __balance
```
In this example the BankAccount class encapsulates the account number as private attributes. These cannot be accessed directly from outside of the class.
The public methods deposit(), withdraw() and get_balance() ensure that proper checks are done before the balance in updated. This helps to provide a controlled way of accessing the balance outside of the class.


**Abstraction** is essentially simplifying complex entities and hiding unnecessary details, allowing you to focus on what an object does rather than how. Eg:
```python
from abc import ABC, abstractmethod

class Shape(ABC):
	@abstractmethod
	def calculate_area(self):
		pass

	@abstractmethod
	def draw(self):
		pass

class Circle(Shape):
	def __init__(self, radius):
		self.radius = radius

	def calculate_area(self):
		return 3.14 * self.radius * self.radius

	def draw(self):
		print(f"Drawing circle with radius {self.radius}")


class Rectangle(Shape):
	def __init__(self, length, width):
		self.length = length
		self.width = width

	def calculate_area(self):
		return self.length * self.width

	def draw(self):
		print(f"Drawing rectangle with length {self.lenngth} and height 
		{self.height})

def process_shape(shape):
	print("area:", shape.calculate_area())
	shape.draw()

circle = Circle(5)
rectangle = Rectangle(2, 4)

process_shape(circle)
process_shape(rectangle)
```
In this example, the Shape class is abstract and contains two abstract methods. *It is abstract because it contains one or more abstract methods.*
The Circle and Rectangle classes inherits from the Shape class and then provide implementations for the abstract methods.
The process_shape() function demonstrates abstraction by accepting a Shape object without knowing the specific type of the shape.

____________________________________________________________________

# API

An **API** is an Application Programming Interface. Is is a set of rules and protocols that allows different applications to communicate and interact.

**Interfacing with external services**
APIs are often used to connect with external services or platforms such as data providers or social media platforms.

**Data exchange**
APIs facilitate the exchange of data between different applications or systems, defining the data formats in which data is sent and received. This makes it easier for applications to understand each other's data

**Standardisation**
By defining clear rules and methods, APIs are able to standardise the interactions with a system, ensuring consistent behaviour and preventing compatibility issues.

**Security and access control**
APIs often include authentication and access control to restrict access to certain functionalities.

**Versioning**
API versioning allows developers to keep using older versions whilst also allowing newer applications to use the latest features.

____________________________________________________________________

# Algorithm

An **algorithm** is a set of instructions used to solve a specific problem. Algorithms take in raw data and output a result after following its set specific steps. 

____________________________________________________________________

# Interpreted/Compiled Languages

In an **interpreted language**, the code is executed line-by-line by at interpreter at runtime. The code is read by the interpreter, translated to machine code and then executed immediately. Python, JavaScript, Ruby and PHP are examples of interpreted languages.

In a **compiled language** the code is all translated to machine code before it is executed. The translation is performed by a compiler which creates an executable file or binary. Compilation errors will occur before runtime.
The generated machine code is then executed by the CPU, running in potentially faster execution. C, C++, Java and Go are examples of compiled languages.

____________________________________________________________________

# Operators

**Operators** are keywords that perform specific operations.

Arithmetic operators: +, -, \*, /, %, ++, --

Comparison operators: \==, !=, >, <, >=, <=

Logical operators: &&, ||, !

Bitwise operators: &, |, ^, ~, <<, >>

____________________________________________________________________

# Data Types

**Data types** define the type of data that can be stored in a variable or used in a program.
Some examples of data types are: integer, float, char, bool, array

____________________________________________________________________

# Frameworks and Libraries

A **framework** is a prebuilt set of tools, components and rules that provide a foundation for developing applications. The application is build by extending and customising the framework.

A **library** is a collection of prebuilt functions or modules that can be used to perform specific tasks.

____________________________________________________________________

# CI/CD Pipelines
A **CI/CD pipeline** is a set of practices that facilitate the continuous integration and continuous delivery of applications. They help to ensure that changes to the codebase are quickly and safely integrated, tested and delivered to end-users.

CI involves frequent automated integration of code changes. When code changes are pushed to the repository, a CI server automatically triggers a set of tasks, including compilation and testing. The main purpose of CI is to detect integration issues as early as possible.

CD is the practice of automating the release and deployment process after successful CI. The software should always be in a state where it could be released to production, although the decision is usually manual.

____________________________________________________________________

