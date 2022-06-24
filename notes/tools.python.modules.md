---
id: pnefbnpwozt81nlk75gogmk
title: Modules
desc: ''
updated: 1649422158886
created: 1649421971544
---

In python each set of functions and classes can be built into a self-contained module. Some of these are standard modules such as `maths` or `random`, some you have to install using `pip` such as `pandas`, or you can create your own by simply saving them in a `.py` file.

To import a module that is not built-in you use the `import` keyword, optionally choosing to alias the module. You can also load just specific classes or functions from a module using the `from` keyword.

```python
import random as rdm
import sys, os, math

from math import sin
```
