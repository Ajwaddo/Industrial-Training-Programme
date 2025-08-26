# Proper Python

- [Proper Python](#proper-python)
  - [Funtion \& Definition](#funtion--definition)
    - [Def](#def)
    - [Return](#return)
    - [Lambda](#lambda)
    - [Yield](#yield)
    - [Pass](#pass)
  - [Control Flow](#control-flow)
    - [If/Elif/Else](#ifelifelse)
    - [For](#for)
    - [While](#while)
    - [Break](#break)
    - [Continue](#continue)
  - [Error Handling](#error-handling)
    - [Try/Except](#tryexcept)
    - [Finally](#finally)
    - [Raise](#raise)
    - [Assert](#assert)
  - [OOP](#oop)
    - [Class](#class)
    - [Self](#self)
    - [\_init\_\\](#_init_)
    - [super()](#super)
    - [del](#del)
  - [Import \& Modules](#import--modules)
    - [Import](#import)
    - [from …. Import …](#from--import-)
    - [as](#as)
  - [Variable Scope \& References](#variable-scope--references)
    - [global](#global)
    - [nonlocal](#nonlocal)
    - [is](#is)
    - [in](#in)
  - [Context \& Special Uses](#context--special-uses)
    - [with](#with)
    - [None](#none)
    - [True/False](#truefalse)
    - [and/or/not](#andornot)


Python Documentation
This documentation provides a more detailed reference for fundamental Python concepts, expanding on the topics you've outlined.

Functions & Definitions
`def`
The `def` keyword is used to define a function. A function is a named block of reusable code that performs a specific task. By using functions, you can make your code more organized, readable, and modular. Functions can accept zero or more inputs, known as arguments, and they can return an output.

```

A simple function with one parameter
def greet(name):
print(f"Hello, {name}!")

Calling the function with an argument
greet("Alice")

Output: Hello, Alice!
A function with a default parameter
def say_hello(name="World"):
print(f"Hello, {name}!")

say_hello()

Output: Hello, World!
say_hello("Bob")

Output: Hello, Bob!
```

`return`
The `return` statement is used to exit a function and send a value back to the caller. A function can return any Python object, and if it doesn't have an explicit `return` statement, it implicitly returns None. You can also return multiple values, which Python handles by packaging them into a tuple.

```
def add_and_subtract(a, b):
# This function returns a tuple of two values
return a + b, a - b

sum_result, diff_result = add_and_subtract(10, 5)
print(f"Sum: {sum_result}, Difference: {diff_result}")

Output: Sum: 15, Difference: 5
def do_nothing():
# This function implicitly returns None
pass
result = do_nothing()
print(result)

Output: None
```

`lambda`
A `lambda` function is a small, anonymous function that can take any number of arguments but is restricted to a single expression. They are called anonymous because they don't have a name. `lambda` functions are typically used for short, one-time operations and are often passed as arguments to other functions like `map()`, `filter()`, or `sorted()`.

```

A lambda function to add two numbers
add = lambda x, y: x + y
print(add(2, 3))

Output: 5
Using a lambda function with the sorted() function
points = [(1, 2), (0, 1), (3, 0)]

Sort the list of tuples based on the second element
sorted_points = sorted(points, key=lambda p: p[1])
print(sorted_points)

Output: [(3, 0), (0, 1), (1, 2)]
```

`yield`
The `yield` keyword is used to create a generator function. Unlike `return`, which terminates a function, `yield` pauses its execution, saves its state, and returns a value to the caller. When the generator is iterated over again (e.g., with `next()`), the function resumes from where it left off. Generators are highly memory-efficient as they produce items one by one instead of creating a full list in memory, making them ideal for handling large datasets.

```
def fibonacci_generator(limit):
a, b = 0, 1
while a < limit:
yield a
a, b = b, a + b

Create a generator object
fibs = fibonacci_generator(10)

Iterate through the generator
print(next(fibs))

Output: 0
print(next(fibs))

Output: 1
print(next(fibs))

Output: 1
print(next(fibs))

Output: 2
Generators can also be used in for loops
print("All fibonacci numbers up to 10:")
for num in fibonacci_generator(10):
print(num)

Output:
All fibonacci numbers up to 10:
0
1
1
2
3
5
8
```

`pass`
The `pass` statement is a null operation. It does absolutely nothing. It is used as a placeholder when a statement is syntactically required but you don't want any code to be executed. This is useful for defining empty functions, classes, or conditional blocks that will be filled in later.

```

A function to be implemented later
def placeholder_function():
pass

An empty class
class EmptyClass:
pass

A conditional block that does nothing
if 1 > 0:
pass
else:
print("This will not be printed")
```

Control Flow
`if`/`elif`/`else`
These keywords are used for conditional execution, allowing your program to make decisions based on specific conditions. The conditions are evaluated in order. The first block whose condition evaluates to True is executed, and the rest of the chain is skipped. The `else` block is a final fallback that runs only if all preceding `if` and `elif` conditions are False.

```
temperature = 25

if temperature > 30:
print("It's a hot day!")
elif temperature > 20:
# This block executes because the first condition is False
# and this one is True
print("It's a nice day.")
else:
print("It's a bit chilly.")

Output: It's a nice day.
```

It is important to note that an `if` statement is mandatory to start a conditional block. You cannot begin a conditional statement with `elif` or `else`.

This will result in a SyntaxError.

```

This will result in a SyntaxError
elif temperature > 20:
print("This won't work!")
else:
print("Neither will this.")

Output: SyntaxError: invalid syntax
```

`for`
A `for` loop is used to iterate over a sequence of items. It executes a block of code once for each item in the sequence. It's a powerful tool for working with lists, tuples, dictionaries, strings, and other iterable objects. The `range()` function is often used to generate a sequence of numbers for a `for` loop.

```
fruits = ["apple", "banana", "cherry"]
for fruit in fruits:
print(f"I have a {fruit}.")

Output:
I have a apple.
I have a banana.
I have a cherry.
Using a for loop with the range() function
for i in range(3):
print(f"Iteration number: {i}")

Output:
Iteration number: 0
Iteration number: 1
Iteration number: 2
```

`while`
A `while` loop repeatedly executes a block of code as long as its condition remains True. It's essential to include a statement within the loop that will eventually make the condition False to avoid an infinite loop.

```
count = 0
while count < 3:
print(f"Count is {count}")
count += 1

Output:
Count is 0
Count is 1
Count is 2
```

`break`
The `break` statement is used to immediately exit the innermost `for` or `while` loop that contains it. The program then continues execution from the first statement after the loop.

```
for i in range(10):
if i == 5:
print("Breaking the loop at 5")
break
print(i)

Output:
0
1
2
3
4
Breaking the loop at 5
```

`continue`
The `continue` statement skips the rest of the code inside the current iteration of a loop and moves on to the next iteration. It's useful when you want to skip certain items in a sequence without exiting the loop entirely.

```
for i in range(5):
if i == 2:
print("Skipping number 2")
continue
print(i)

Output:
0
1
Skipping number 2
3
4
```

Error Handling
`try`/`except`
The `try` and `except` blocks are used for handling runtime errors (exceptions). Code that might raise an error is placed inside the `try` block. If an error occurs, the code inside the `except` block is executed instead of the program crashing. You can catch specific exceptions to handle different error types gracefully.

```
try:
# This line will cause a ZeroDivisionError
result = 10 / 0
except ZeroDivisionError:
# This block handles the specific error
print("Error: Cannot divide by zero!")
except TypeError:
# This block would handle a different type of error
print("Error: Type mismatch!")
except Exception as e:
# This is a general catch-all for any other exception, and 'as e' gives you
# access to the error message.
print(f"An unexpected error occurred: {e}")

Output: Error: Cannot divide by zero!
```

`finally`
The `finally` block is an optional addition to a `try...except` block. The code inside the `finally` block will always be executed, whether an exception occurred or not. This is particularly useful for cleanup actions, such as closing a file or a database connection, ensuring that resources are released properly.

```
try:
file = open("test_file.txt", "w")
file.write("Hello, world!")
# The program will crash here if we try to divide by zero
# a_list = [1, 2]
# print(a_list[5])
except IOError:
print("An IOError occurred.")
finally:
# This will always be executed, closing the file
print("Closing the file.")
file.close()

Output:
Closing the file.
```

`raise`
The `raise` statement allows you to manually force a specific exception to occur. This is useful for indicating that a function has received invalid input or that some other condition has been violated, preventing the program from continuing with bad data.

```
def set_age(age):
if not isinstance(age, int):
# Raise a TypeError if the input is not an integer
raise TypeError("Age must be an integer.")
if age < 0:
# Raise a ValueError if the age is negative
raise ValueError("Age cannot be negative.")
print(f"Age set to {age}.")

try:
set_age("twenty")
except (TypeError, ValueError) as e:
print(f"An error occurred: {e}")

Output: An error occurred: Age must be an integer.
```

`assert`
The `assert` statement is a debugging tool used to check if a condition is true. If the condition is False, it raises an `AssertionError` with an optional error message. It's a quick way to ensure that assumptions about your code are met, and it's typically used to catch programmer errors rather than user errors.

```
def average(numbers):
# Assert that the input is a non-empty list
assert isinstance(numbers, list) and len(numbers) > 0, "Input must be a non-empty list."
return sum(numbers) / len(numbers)

print(average([10, 20, 30]))

Output: 20.0
try:
print(average([]))
except AssertionError as e:
print(f"Assertion Error: {e}")

Output: Assertion Error: Input must be a non-empty list.
```

Object-Oriented Programming (OOP)
`class`
A class is a blueprint for creating objects. It encapsulates data (attributes) and functionality (methods) into a single unit. Attributes are variables that store information about an object, and methods are functions that define its behavior.

```
class Dog:
# A class attribute, shared by all instances of the class
species = "Canis familiaris"

# The __init__ method (constructor) initializes instance attributes
def __init__(self, name, age):
    self.name = name  # Instance attribute
    self.age = age    # Instance attribute

# An instance method
def bark(self):
    return f"{self.name} says Woof!"

Create an object (an instance) of the Dog class
my_dog = Dog("Fido", 5)
print(f"My dog's name is {my_dog.name} and it is a {my_dog.species}.")

Output: My dog's name is Fido and it is a Canis familiaris.
```

`self`
The `self` parameter is a convention in Python to refer to the instance of the class that a method belongs to. It is the first parameter of any instance method, and it automatically gets passed the instance object when the method is called. Using `self`, you can access and modify the attributes and methods of the specific object.

```
class Car:
def init(self, color):
self.color = color  # self.color is an instance attribute

def get_color(self):
    # self refers to the specific Car object
    return self.color

my_car = Car("Red")
other_car = Car("Blue")

print(my_car.get_color())

Output: Red
print(other_car.get_color())

Output: Blue
```

`init`
The `init` method, often called the constructor, is a special method that is automatically called when a new object is created from a class. Its primary purpose is to initialize the new object's attributes. You'll use it to set up the initial state of your object.

```
class Book:
def init(self, title, author, pages):
# These are instance attributes initialized by the constructor
self.title = title
self.author = author
self.pages = pages

book1 = Book("The Hitchhiker's Guide to the Galaxy", "Douglas Adams", 208)
print(f"Book: {book1.title}, Author: {book1.author}, Pages: {book1.pages}")

Output: Book: The Hitchhiker's Guide to the Galaxy, Author: Douglas Adams, Pages: 208
```

`super()`
The `super()` function allows a child class to access methods and attributes of its parent class. This is most commonly used in inheritance, especially in the `init` method of a child class, to call the parent's constructor and initialize inherited attributes. This helps to avoid code duplication and maintain a clear hierarchy.

```
class Animal:
def init(self, name, sound):
self.name = name
self.sound = sound

def make_sound(self):
    print(f"{self.name} says {self.sound}")

class Dog(Animal):
def init(self, name, breed):
# Call the parent class's constructor to initialize 'name'
# We pass 'Woof' as the sound to the parent's init method
super().init(name, "Woof")
self.breed = breed

def make_sound(self):
    # This calls the method from the parent class (Animal)
    super().make_sound()
    print(f"This is a {self.breed}.")

my_dog = Dog("Fido", "Golden Retriever")
my_dog.make_sound()

Output:
Fido says Woof
This is a Golden Retriever.
```

`del`
The `del` keyword is a statement used to delete an object's reference. In the context of classes, you can use it to delete an object's attribute or the object itself. When all references to an object are deleted, Python's garbage collector will eventually remove the object from memory.

```
class Person:
def init(self, name):
self.name = name

p1 = Person("Alice")
p2 = p1 # p2 is now another reference to the same object

Delete the attribute 'name' from the object
del p1.name

print(p1.name) # This would raise an AttributeError
Delete the reference 'p1'
del p1

print(p1) # This would raise a NameError
However, p2 still exists and refers to the object
print(p2)
```

Import & Modules
`import`
The `import` statement is used to import a module, which is a file containing Python code. This makes the module's functions, classes, and variables available in your current file. To use an imported item, you must prefix it with the module name.

```

Imports the entire 'math' module
import math

print(math.sqrt(16))

Output: 4.0
Imports the entire 'random' module
import random

print(random.randint(1, 10))

Output: (a random integer between 1 and 10)
```

`from ... import ...`
This statement is used to import specific items (functions, classes, or variables) from a module directly into your current namespace. This allows you to use the imported items without needing to prefix them with the module name, which can make your code cleaner. Be cautious, as this can lead to name conflicts if you import multiple items with the same name.

```

Imports only the 'pi' variable from the 'math' module
from math import pi

print(pi)

Output: 3.141592653589793
Imports the 'randint' function from the 'random' module
from random import randint

print(randint(1, 10))

Output: (a random integer between 1 and 10)
```

`as`
The `as` keyword is used to create an alias or a shorter name for an imported module or item. This is a common practice for modules with long names (e.g., `import pandas as pd`) or for resolving name conflicts when importing from different modules.

```

Create an alias 'pd' for the 'pandas' module
import pandas as pd

Create an alias 'get_random_int' for the 'randint' function
from random import randint as get_random_int

Now you can use the aliases
data = pd.DataFrame({'col1': [1, 2]})
print(data)
print(get_random_int(1, 5))
```

Variable Scope & References
`global`
Variables defined outside of a function are considered to be in the global scope. The `global` keyword is used inside a function to explicitly declare that a variable is a global one, and that you intend to modify it. Without the `global` keyword, any assignment to a variable inside a function will create a new, local variable with the same name.

```
x = 10  # This is a global variable

def modify_global():
# 'x' inside this function refers to the global variable
global x
x += 5
print(f"Inside function, x is: {x}")

modify_global()

Output: Inside function, x is: 15
print(f"Outside function, x is: {x}")

Output: Outside function, x is: 15
```

`nonlocal`
The `nonlocal` keyword is similar to `global` but is used in nested functions. It declares that a variable is not local to the inner function, but rather belongs to an enclosing function. It allows you to modify a variable in an outer, non-global scope.

```
def outer_function():
count = 0  # This is a variable in the outer function's scope

def inner_function():
    # 'nonlocal' refers to 'count' in the outer_function's scope
    nonlocal count
    count += 1
    print(f"Inner function count: {count}")

inner_function()
# Output: Inner function count: 1
inner_function()
# Output: Inner function count: 2
return count

final_count = outer_function()
print(f"Final count is: {final_count}")

Output: Final count is: 2
```

`is`
The `is` operator checks for object identity. It returns True if two variables refer to the exact same object in memory, and False otherwise. This is different from the `==` operator, which checks for value equality. Use `is` when you need to confirm if two variables are pointing to the same instance of an object.

```
a = [1, 2, 3]
b = a          # b and a refer to the same list object
c = [1, 2, 3]  # c is a new list object with the same values

print(f"a is b: {a is b}")

Output: a is b: True
print(f"a == c: {a == c}")

Output: a == c: True (Their values are equal)
print(f"a is c: {a is c}")

Output: a is c: False (They are different objects)
```

`in`
The `in` operator checks for membership. It returns True if an item is found within a sequence (like a list, tuple, set, or string) and False otherwise. It's a simple and readable way to test for the existence of an element.

```
fruits = ["apple", "banana", "cherry"]
print(f"'banana' in fruits: {'banana' in fruits}")

Output: 'banana' in fruits: True
print(f"'grape' in fruits: {'grape' in fruits}")

Output: 'grape' in fruits: False
text = "Hello, World!"
print(f"'World' in text: {'World' in text}")

Output: 'World' in text: True
```

Context & Special Uses
`with`
The `with` statement is a powerful construct for simplifying resource management. It guarantees that a resource, such as an open file or a network connection, is properly acquired at the beginning of a block and automatically released at the end, even if an error occurs.

```

The with statement automatically handles opening and closing the file
with open("notes.txt", "w") as file:
file.write("This is a line of text.\n")
file.write("This is another line.\n")

The file is automatically closed here, even if a crash occurred inside the block.
```

`None`
`None` is a special constant that represents the absence of a value. It is the sole instance of the `NoneType` data type. It is not the same as `0`, an empty string, or False. It is often used to initialize variables or to indicate that a function does not return a meaningful value.

```
my_variable = None
if my_variable is None:
print("The variable has no value assigned.")

Output: The variable has no value assigned.
```

`True`/`False`
True and False are the two boolean values that represent the truth values of expressions. They are used in conditional statements and logical operations to control the flow of a program.

```
is_sunny = True
is_cold = False

if is_sunny and not is_cold:
print("It's a perfect day!")

Output: It's a perfect day!
```

`and`/`or`/`not`
These are the three logical operators that are used to combine and manipulate boolean expressions.

and: Returns True if both of its operands are True.

or: Returns True if at least one of its operands is True.

not: Reverses the boolean value of its operand.

```
age = 25
has_license = True
is_senior = False

and example
if age >= 16 and has_license:
print("You are eligible to drive.")

Output: You are eligible to drive.
or example
if is_senior or age >= 65:
print("You qualify for a senior discount.")

Output: (nothing is printed)
not example
if not is_senior:
print("You are not a senior.")

Output: You are not a senior.
```