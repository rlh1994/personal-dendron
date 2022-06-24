---
id: o5gq12vklw12ni3jaz75vi0
title: Functions
desc: ''
updated: 1650460140604
created: 1650446508193
---

# Functions
Functions are re-usable snippets of code that can be called with a single line. They can take arguments and return an object (or `None`). You define a function using the `def` keyword as follows

```python
def hello():
    print('Howdy')
    print('Howdy!')
    print('Hello there')
```
This example function takes no arguments and returns no objects; a more complicated function could be
```python
def multiply(x: float, y:float) -> float:
    return x*y
```
where we are using type hints in the definition. Note that these aren't enforced in any way and will not throw a `TypeError` if not followed. You can also use the [typing](https://docs.python.org/3/library/typing.html) module if you want autocomplete and IDE type checkers to run for your functions.

## Function scope
Variables that are created within the function only exist within the call of the function itself - once the function has completed those variables are destroyed and are not accessible (unless you declare them as global variables). 

If you need to call/modify a global variable within a function you can do this using the `global` keyword

```python
def change_x():
    global x
    x = 7

x = 5
change_x()
print(x) # 7
```

## Side Effects
In python functions can cause _side effects_ which is where the function _does_ something outside the scope of the function; generally there are 3 types of side effects:
1. The function prints something to some output (often a desired side effect)
2. The function changes the value of a mutable object e.g. a list
3. The function changes the value of a global variable

Often 1 and 3 have to be done on-purpose and are unlikely to happen by accident, but 2 can be very confusing due to the nature by which objects are passed to functions based on if they are [[mutable|tools.python.types#mutable]] or not. 

> **Pass by value**  
> When objects are passed by value to a function, the _content_ of an object is passed to the function and stored in a new local object - any changes to this object do not impact the object that was first passed

> **Pass by reference**  
When objects are passed by reference to a function, the _location_ of an object is passed to the function and used - any changes to the object at this location impact the object outside the function as the variable for that object also points to that location.

> **Pass by object reference**  
> Python goes one step further to confuse things, it doesn't pass by reference entirely but passes the object by reference. To understand this think of a list (the variable that contains an object) as a box that stores the object(s) inside it. Python will pass the location of the contents of this box to the function but the function will have it's own box - changes to the contents in one box change the contents of the other box (because they both look at the same thing...).

Overall when a variable is passed to a function, the object that variable is pointing to (not the location of the variable) itself is passed in it's place, for immutable objects this is fine, for mutable ones less so.

Most functions that are provided in e.g. `pandas` tend to avoid these, and reserve changing a variables values to a method instead of a function, but when writing your own functions you should be careful of this.
