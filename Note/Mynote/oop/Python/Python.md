## Table Content
- [Basic Syntax](#basic-syntax)
- [Print Statement](#print-statement)
- [Input from User](#input-from-user)
- [Conditional Statements](#conditional-statements)
- [Loops](#loops)
- [Functions](#functions)
- [Basic Data Structures](#basic-data-structures)
- [Exception Handling](#exception-handling)
- [Common Built-in Functions](#common-built-in-functions)
- [Basic File IO](#basic-file-io)

## Basic Syntax
- Indentation: Python uses indentation. Unlike other languages, there are no curly braces {}.
```python
if True:
    print("This is indented correctly")
```

- Comments: Use # for single-line comments, and triple quotes ''' or """ for multi-line comments.
```python
# This is a single-line comment
"""
This is a
multi-line comment
"""
```

- Variables: No need to declare variable types explicitly. Variables are created when a value is assigned.
```python
x = 10  # integer
name = "Waiyat"  # string
```
- Data Types:
1) int: Integer
2) float: Floating point number
3) str: String
4) bool: Boolean (True or False)
5) list: Ordered collection
6) dict: Dictionary, key-value pairs


## Print Statement
print() is used to output text or variables
```python
print("Hello, World!")
age = 32
print("Age:", age)
```

## Input from User
Use input() to get user input.
```python
name = input("Enter your name: ")
print("Hello, " + name)
```

## Conditional Statements
- if, elif, and else
```python
age = 18
if age >= 18:
    print("You're an adult!")
elif age > 12:
    print("You're a teenager.")
else:
    print("You're a child.")
```

- Comparison Operators:
1) == Equal
2) != Not equal
3) > Greater than
4) < Less than
5) >= Greater than or equal to
6) <= Less than or equal to

- Logical Operators:
1) and: True if both conditions are true
2) or: True if at least one condition is true
3) not: Reverses the truth value


## Loops
- for Loop: Iterates over a sequence (like a list, range, or string).
```python
for i in range(5):  # range(5) gives 0, 1, 2, 3, 4
    print(i)
```
- While Loop: Repeats as long as the condition is true.
```python
count = 0
while count < 5:
    print(count)
    count += 1
```
- Break and Continue:
```python
for i in range(5):
    if i == 3:
        break  # Exit the loop when i is 3
    print(i)
```


## Functions
- Define functions using def.
```python
def greet(name):
    print("Hello, " + name)

greet("Waiyat")
```

- Return values from functions using return.
```python
def add(a, b):
    return a + b

result = add(5, 3)
print(result)  # Output: 8
```

## Basic Data Structures
- List: Ordered, mutable collection of items.
```python
my_list = [1, 2, 3, "apple"]
my_list.append(4)  # Adds 4 to the list
print(my_list)
```

- Dictionary: Key-value pairs.
```python
my_dict = {"name": "YuQi", "age": 25}
print(my_dict["name"])  # Output: YuQi
my_dict["age"] = 26  # Update value
```

## Exception Handling
Handle errors using try, except
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("You can't divide by zero!")
```

## Common Built-in Functions
- len(): Get the length of a list, string, or other collections.
- type(): Get the type of a variable.
- str(), int(), float(): Convert between types.
```python
print(len("Hello"))  # Output: 5
print(type(5))  # Output: <class 'int'>
```

## Basic File IO
- Reading a file:
```python
with open("file.txt", "r") as file:
    content = file.read()
    print(content)
```

- Writing to a file:
```python
with open("file.txt", "w") as file:
    file.write("Hello, World!")
```