---
id: b81scqd1lhhhovvfanixvyx
title: Exceptions
desc: ''
updated: 1650466116898
created: 1650465944614
---

Exceptions in python can be of multiple types and are referred to as **errors**. Some common types include `ZeroDivisionError`, `TypeError`, and `IndexError`. You can catch these in a `try/except` block:

```python
def spam(divideBy):
    try:
        return 42 / divideBy
    except ZeroDivisionError:
        print('Error: Invalid argument.')
```
Note that anything after the line raising the error in the `try` block will not be executed.
