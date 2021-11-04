## Python

#### Syntax:

- no semicolons at the end of line

- loops:

  - for i in list:
  
  - for i in range(to_val):

- range of values: range(to, from, stepsize), returns a generator

- comments: #

- coding style:

  - indentation: 4 spaces
  - separate functions and classes by a line
  - lower_case for variables and functions, CamelCase for classes

#### Data types:

- can be returned with the type() method

- numbers: int, float, complex

  - casting: int(x)
  - *useful methods:*
    - pow (or n**k), abs, round
  - modules: 
    - math - pow, trigonometric functions, constants, logarithmic functions
    - statistics - statistical functions
    - random - random, choice, shuffle

- strings

  - str(x)

  - can be joined by +

  - formatting:

    ```python
    myorder = "I want {} pieces of item {} for {} dollars"
    print(myorder.format(quantity, itemno, price))
    ```

  - \n is a newline

  - *useful methods:*

    - checks: isnum, isalnum, isupper, islower
    - modifications: rstrip, lstrip, join, split, find (substring), index (substring), replace, lower, upper 

- booleans: True and False 

#### Operators:

	- arithmetic: +, -, /, *
	- comparison: >, <, >=, <=
	- exponent: **
	- logical: and, or

#### Lists:

- list = [“this”,”is”,”a”,”list”]

- mylist.append(), .remove(), .sum()

- .sort(key=“reverse”)

  - can also implement custom keys for sorting 

- list comprehensions:

  - instead of a for loop to get items out of a list

  - ```python
    [v for v in my_list if v >= 100]
    ```

- slicing lists: mylist[:2], mylist[:-1] (first value)

- itertools has all sorts of functions for lists:

  - ```python
    flatter_list = list(itertools.chain.from_iterable(mylist))
    ```

- ```python
  for i, el in enumerate(mylist):
  ```
  - enumerator returns index of value and value in list

#### Dictionaries:

- {key: value, key: value, key:value}

- ```python
  mydict.keys()                         
  mydict.values()                      
  mydict.items()                        
  ```

- dict(collection)

- To get value for a key: value = dict.pop(key)

#### Sets:

- set1 = set()
- can get unique values from a list
- frozenset - immutable, can be used as a key

#### Tuples:

- immutable list of 2 values

#### Function definitions:

- ```python
  def multiply(a,b):
    return a*b
  ```

- \* unpacks argument lists 

- ```python
  def add(*a):
      return sum(a)
  ```

- ^ running add(1,2,3) will return 6

- ** unpacks arguments into key-value pairs

- ```python
  date_info = {'year': "2020", 'month': "01", 'day': "01"}
  filename = "{year}-{month}-{day}.txt".format(**date_info)
  ```

#### Classes:

- Create a type of object and allows to make instances
  
- e.g. x = MyClass()
  
- Class structure:

  ```python
  class Vector:
      def __init__(self,vector):
          self.values = vector
          self.length = len(vector)
      def dot(self,b):
          return self.x*b.x+self.y*b.y+self.z*b.z
  ```

- Inheritance:

  - ```python
    class Person:
        def __init__(self, name, age):
            self.name = name
            self.age  = age
    class Employee(Person):
        def __init__(self, name, age, staff_num):
            super().__init__(name, age)
            self.staff_num = staff_num
    
    ```

#### Files:

- ```python
  myfile = open(mypath, mode='r', encoding=None, newline=None)
  ```

- r, w - read and write modes
- a - append
- .readlines()
- paths: os.path.join will join path components

#### Regular expressions

- ```python
  # password check regex
  # ^ = start of string
  # ?= looks ahead, .* = zero or more of any char
  # patterns: [A-Z]/[a-z] = upper/lowercase letters, [0-9] = numbers
  # [A-Za-z0-9] combines all allowed types and {6,} checks that they appear 6+ times
  # $ = end of string
  regex="^(?=.*[A-Z])(?=.*[a-z])(?=.*[0-9])[A-Za-z0-9]{6,}$"
  ```

#### Useful modules:

- datetime
- re (regular expressions)
- collections (has different data types like counter or named tuple)
- tkinter (GUI)
- csv (managing CSV files)
- time (to time code)