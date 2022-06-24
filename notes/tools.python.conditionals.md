---
id: vprzfprdxm2ehupurhylg2p
title: Conditionals
desc: ''
updated: 1649418685978
created: 1649418475206
---

# IF statements
`if` statements let you conditionally run parts of your code. The decision is made by a Boolean value that can be the output of a comparison expression using `==`, `>=`, `>`, `<`, `<=`, `!=`. 

```python
if 4 > 2:
    print('Maths works!')
```

You can extend this to multiple branches using `elif` and ending with a default `else`. Note that it runs checks in order and will only run the first `true` condition it hits.

```python
if name == 'Alice':
    print('Hi, Alice.')
elif age < 12:
    print('You are not Alice, kiddo.')
else:
    print('You are neither Alice nor a little kid.')
```
