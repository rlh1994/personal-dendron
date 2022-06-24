---
id: 47gwqwta0q1vzcl23ylbz8p
title: Types
desc: ''
updated: 1650447664798
created: 1648540508834
---

# Built-In Types
## Strings
[Strings](https://docs.python.org/3/library/stdtypes.html#text-sequence-type-str) are an **immutable** built in type in python can be created using single quotes `'` or double quotes `"`, or for multiline strings (with intact whitespace) you can use triple quotes `'''` or `"""`. They have many methods for manipulating strings which can be found in the docs.

### f strings
Formatting strings in python used to involve either a complex `%` operation, or using the `str.format()` method. These were okay but not ideal. Since python 3.6 the preferred method is to use f-strings. f-strings are a string that starts with the letter `f` before the quotes and within which anything between curly brackets (`{}`) is run as python code inline within the string.

```python
myName = input()
print(f"Hello {myName}, it is nice to meet you")
```

## Integer


## Float

## Boolean
There are 2 Boolean values, `True` and `False`.

Other values can be truth or false like, for example:
- `0`, `0.0`, `''` are all evaluated as `False`
- Most other values are evaluated as `True`

These can be combined using the `and`, `or` and `not` keywords.

# Type Properties
## Iterable
Objects that are containers with a countable number of values are iterable. These include lists, tuples, dictionaries, and sets. Any custom class with a `__iter__()` and `__next__()` methods are iterable. 

To create an iterator from an iterable (i.e. one that will be only a single value at each call) you use the `iter(my_iterable)` method and call the next value using the handily named `next(my_iterator)` method!

```python
mytuple = ("apple", "banana", "cherry")
myit = iter(mytuple)

print(next(myit))
print(next(myit))
print(next(myit))
```

## Mutable 
Types which are mutable can be edited in place without having to first create a new object. Immutable objects on the other hand cannot be edited once they have been created and so a new variable needs to be created.

```python
# valid editing of a mutable object
mylist = [1, 2, 3]
mylist[1] = 5
print(mylist)
# [1, 5, 3]

# invalid editing of an immutable object
mystring = 'hello'
mystring[3] = 'q'
# TypeError: 'str' object does not support item assignment
```
