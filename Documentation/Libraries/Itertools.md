[⬅](../../README.md)
# Itertools Documentation
## Contents
- [Methods](#methods)
  - [Accumulate](#accumulate)
- [Common Usages](#common-usages)

[🔼](#itertools-documentation)
## Methods

[🔼](#itertools-documentation)
### Accumulate

```python
iterator = itertools.accumulate(iterable, func = sum, initial = None)
```
Used to compute the cumulative sum or other function from the iterable.
It returns an iterator, which does not precompute all the values, but instead generates them od demand.
Using list on the iterator consumed the whole thing, generating the fill list.

Examples
```python
>>> from itertools import accumulate
>>> list(accumulate([1, 3, 5])
[1, 4, 9]
>>> import operator
>>> list(accumulate([1, 3, 5], operator.mul)
[1, 3, 15]
>>> list(accumulate([10, 3, 2, 4], operator.sub)
[10, 7, 5, 1]
>>> list(accumulate([100, 2, 2], operator.truediv)
[100, 50, 25]
>>> list(accumulate([1, 3, 2, 5], max)
[1, 3, 3, 5]
>>> list(accumulate([2, 1, 3], min)
[2, 1, 1]
>>> list(accumulate([1, 2, 3, lambda x, y: (x + y) * 2))
[1, 6, 18]
>>> def fib(x, y): return x + y
>>> list(accumulate([0, 1, 2, 3], fib))
[0, 1, 3, 6]
```

[🔼](#itertools-documentation)
## Common Usages
