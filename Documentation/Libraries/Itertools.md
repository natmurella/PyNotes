[⬅](../../README.md)
# Itertools Documentation
## Contents
- [Methods](#methods)
  - [Infinite Iterators](#infinite-iterators)
    - [Count](#count)
  - [Terminating Iterators](#terminating-iterators)
    - [Accumulate](#accumulate)
  - [Combinatoric Iterators](#combinatoric-iterators)
    - [Product](#product)
- [Iterator Usage](#iterator-usage)
  - [Next](#next)
  - [For Loop](#for-loop)
  - [List](#list)
  - [Zip](#zip)
  - [Map](#map)
  - [Build-In Functions](#build-in-functions)
- [Common Usages](#common-usages)

[🔼](#itertools-documentation)
## Methods

[🔼](#itertools-documentation)
### Infinite Iterators

[🔼](#itertools-documentation)
#### Count

```python
iterator = itertools.count(start = 0, step = 1)
```
make an iterator that generates evenly spaced values (separated by step) beginning with start.

Example:
```python
>>> for i in itertools.count()
0
1
2
...
```
```python
>>> for i in itertools.count(2, 0.5)
2.0
2.5
3.0
...
```

[🔼](#itertools-documentation)
### Terminating Iterators

[🔼](#itertools-documentation)
#### Accumulate

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
### Combinatoric Iterators

[🔼](#itertools-documentation)
#### Product

```python
iterator = itertools.product(*iterables, repeat=1)
```
Cartesian product of the iterables. Roughly equivalent to nested for-loops in a generator expression. 
For example, product(A, B) returns the same as ((x,y) for x in A for y in B).
The Repeat meant taking the iterables with themselves n times (default 1)

Example:
```python
>>> product("AB", "xy")
[(A,x), (A,y), (B,x), (B,y)]
>>> product([1, 2], repeat=2)
[(1, 1), (1, 2), (2, 1), (2, 2)]
>>> product([1, 2, 3], repeat=3)
[(1, 1, 1), (1, 1, 2), (1, 2, 1), (1, 2, 2), (2, 1, 1), (2, 1, 2), (2, 2, 1), (2, 2, 2)]
```


[🔼](#itertools-documentation)
## Iterator Usage

[🔼](#itertools-documentation)
## Common Usages
