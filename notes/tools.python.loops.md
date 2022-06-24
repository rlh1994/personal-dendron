---
id: yxk6ks3z3e92xt4pyz8bll1
title: Loops
desc: ''
updated: 1649421895068
created: 1648540240401
---

# While loops
`while` loops in python use the keyword followed by the `condition` then the `:`. 

`break` is used to immediately exit out of the loop once the command is reached.

`continue` is used to skip the rest of the current iteration and start the next cycle of the loop.

```python
while True:
    print('Who are you?')
    name = input()
    if name != 'Joe':
        continue
    print('Hello, Joe. What is the password? (It is a fish.)')
    password = input()
    if password == 'swordfish':
        break
print('Access granted.')
```

# For loops

For loops will run a fixed amount of times over an [[iterator|tools.python.types#iterable]] with one run per value in that iterator. You can also use the `range` function to generate a range object that you can iterate over. `range` takes up to 3 arguments; `start`, `stop`, `step` and will not include the `stop` value in the output.

```python
print('My name is')
for i in range(5):
    print(f'Jimmy Five Times ({str(i)})')
```
