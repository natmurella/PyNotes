# Itertools Documentation
[⬅](../../README.md)

Functions creating iterators for efficient looping
## Contents
- [Methods](#methods)
  - [Infinite Iterators](#infinite-iterators)
    - [count](#count)
    - [cycle](#cycle)
    - [repeat](#repeat)
  - [Terminating Iterators](#terminating-iterators)
    - [accumulate](#accumulate)
    - [batched](#batched)
    - [chain](#chain)
  - [Combinatoric Iterators](#combinatoric-iterators)
    - [oroduct](#product)
- [Iterator Usage](#iterator-usage)
  - [next](#next)
  - [For Loop](#for-loop)
  - [List](#list)
  - [zip](#zip)
  - [map](#map)
  - [Built-In Functions](#built-in-functions)
- [Common Usages](#common-usages)

[🔼](#itertools-documentation)
## Methods

[🔼](#itertools-documentation)
### Infinite Iterators

[🔼](#itertools-documentation)
#### count

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
#### cycle

```python
iterator = itertools.cycle(iterable)
```

When the iterable is exhausted, return elements from the saved copy. Repeats indefinitely.

```python
>>> cycle('AB')
[A, B, A, B, ...]
```

[🔼](#itertools-documentation)
#### repeat

```python
iterator = itertools.repeat(object, times=None)
```
Makes an iterator that returns the same object infinite times, unless set.

```python
>>> repeat(2)
[2, 2, 2, ...]
>>> repeat(3, 3)
[3, 3, 3]
```


[🔼](#itertools-documentation)
### Terminating Iterators

[🔼](#itertools-documentation)
#### accumulate

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
#### batched

```python
iterator = itertools.batched(iterable, n, strict=false)
```

Batch data from the iterable into tuples of length n. The last batch may be shorter than n. if strict True, error if batch shorter.

```python
>>> batched("abcdef", 2)
[(a, b), (c, d), (e, f)]
```

[🔼](#itertools-documentation)
#### chain

```python
iterator = itertools.chain(*iterables)
```

Make an iterator that returns elements from the first iterable until it is exhausted, then proceeds to the next iterable, until all of the iterables are exhausted.\

```python
>>> chain('ABC', 'DEF')
[A, B, C, D, E, F]
```

[🔼](#itertools-documentation)
### Combinatoric Iterators

[🔼](#itertools-documentation)
#### product

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
#### next

```python
>>> itr = iter([10, 20, 30])
>>> next(itr)
10
>>> next itr
20
```

[🔼](#itertools-documentation)
#### For Loop

```python
my_iterator = iter(range(5))

for number in my_iterator:
    print(number)
```
```python
0
1
2
3
4
```

[🔼](#itertools-documentation)
#### List

```python
>>> my_iterator = iter(range(5))
>>> numbers_list = list(my_iterator)
[0, 1, 2, 3, 4]
```

[🔼](#itertools-documentation)
#### zip

```python
iterator = zip(*iterator)
```
The zip() function returns a zip object, which is an iterator of tuples where the first item in each passed iterator is paired together, and then the second item in each passed iterator are paired together etc.
If the passed iterables have different lengths, the iterable with the least items decides the length of the new iterator.

```python
>>> numbers = iter([1, 2, 3])
>>> letters = iter(['a', 'b', 'c'])
>>> zip(numbers, letters)
[(1, a), (2, b), (3, c)]
```

[🔼](#itertools-documentation)
#### map

```python
iterator = map(function, *iterator)
```

The map() function executes a specified function for each item in an iterable. The item is sent to the function as a parameter.
Make sure the function has a parameter for each iterator.

```python
>>> m = map(lambda x,y: x+y, (a, b), (c, d))
>>> list(m)
[ac, bd]
```

[🔼](#itertools-documentation)
#### Built-In Functions

Many built-in functions expect iterables, so you can use iterators with them as well.

```python
>>> itr = iter([1, 2, 3, 4])
>>> sum(itr)
10
>>> max(itr)
4
>>> min(itr)
1
```
```python
>>> b = iter([True, True, False])
>>> any(b)
True
>>> all(b)
False
```


[🔼](#itertools-documentation)
## Common Usages
