[⬅](../../README.md)
# Functools Documentation
Higher-order functions and operations on callable objects
## Contents
- [Decorators](#decorators)
  - [cache](#cache)
  - [cached_property](#cached-property)
  - [lru_cache](#lru-cache)
  - [total_ordering](#total-ordering)
- [Methods](#methods)
  - [cmp_to_key](#cmp-to-key)
  - [partial](#partial)
  - [partialmethod](#partialmethod)
  - [reduce](#reduce)

[🔼](#functools-documentation)
## Decorators

[🔼](#functools-documentation)
### cache

```python
@functools.cache(user_function)
```

Simple lightweight unbounded function cache. Sometimes called “memoize”.
Returns the same as lru_cache(maxsize=None), creating a thin wrapper around a dictionary lookup for the function arguments. 
Because it never needs to evict old values, this is smaller and faster than lru_cache() with a size limit.

```python
@cache
def factorial(n):
    return n * factorial(n-1) if n else 1

>>> factorial(10)      # no previously cached result, makes 11 recursive calls
3628800
>>> factorial(5)       # just looks up cached value result
120
>>> factorial(12)      # makes two new recursive calls, the other 10 are cached
479001600
```

[🔼](#functools-documentation)
### pached property

```python
@functools.cached_property(func)
```

Transform a method of a class into a property whose value is computed once and then cached as a normal attribute for the life of the instance. 
Similar to property(), with the addition of caching. Useful for expensive computed properties of instances that are otherwise effectively immutable.

```python
class DataSet:

    def __init__(self, sequence_of_numbers):
        self._data = tuple(sequence_of_numbers)

    @cached_property
    def stdev(self):
        return statistics.stdev(self._data)
```

[🔼](#functools-documentation)
## lru cache

```python
@functools.lru_cache(user_function)
@functools.lru_cache(maxsize=128, typed=False)
```

Decorator to wrap a function with a memoizing callable that saves up to the maxsize most recent calls. 
It can save time when an expensive or I/O bound function is periodically called with the same arguments.

Since a dictionary is used to cache results, the positional and keyword arguments to the function must be hashable.

Distinct argument patterns may be considered to be distinct calls with separate cache entries. 
For example, f(a=1, b=2) and f(b=2, a=1) differ in their keyword argument order and may have two separate cache entries.

If user_function is specified, it must be a callable. 
This allows the lru_cache decorator to be applied directly to a user function, leaving the maxsize at its default value of 128:

```python
@lru_cache
def count_vowels(sentence):
    return sum(sentence.count(vowel) for vowel in 'AEIOUaeiou')
```

If typed is set to true, function arguments of different types will be cached separately. 
If typed is false, the implementation will usually regard them as equivalent calls and only cache a single result. 
(Some types such as str and int may be cached separately even when typed is false.)

The wrapped function is instrumented with a cache_parameters() function that returns a new dict showing the values for maxsize and typed. 
This is for information purposes only. Mutating the values has no effect.
To help measure the effectiveness of the cache and tune the maxsize parameter, the wrapped function is instrumented with a cache_info() 
function that returns a named tuple showing hits, misses, maxsize and currsize.
The decorator also provides a cache_clear() function for clearing or invalidating the cache.

In general, the LRU cache should only be used when you want to reuse previously computed values. Accordingly, 
it doesn’t make sense to cache functions with side-effects, functions that need to create distinct mutable objects on each call 
(such as generators and async functions), or impure functions such as time() or random().

```python
@lru_cache(maxsize=32)
def get_pep(num):
    'Retrieve text of a Python Enhancement Proposal'
    resource = f'https://peps.python.org/pep-{num:04d}'
    try:
        with urllib.request.urlopen(resource) as s:
            return s.read()
    except urllib.error.HTTPError:
        return 'Not Found'

>>> for n in 8, 290, 308, 320, 8, 218, 320, 279, 289, 320, 9991:
...     pep = get_pep(n)
...     print(n, len(pep))

>>> get_pep.cache_info()
CacheInfo(hits=3, misses=8, maxsize=32, currsize=8)
```

Example of efficiently computing Fibonacci numbers using a cache to implement a dynamic programming technique:

```python
@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n-1) + fib(n-2)

>>> [fib(n) for n in range(16)]
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, 233, 377, 610]

>>> fib.cache_info()
CacheInfo(hits=28, misses=16, maxsize=None, currsize=16)
```

[🔼](#functools-documentation)
## total ordering

```python
@functools.total_ordering
```

Given a class defining one or more rich comparison ordering methods, this class decorator supplies the rest. 
This simplifies the effort involved in specifying all of the possible rich comparison operations:

The class must define one of __lt__(), __le__(), __gt__(), or __ge__(). In addition, the class should supply an __eq__() method.

```python
@total_ordering
class Student:
    def _is_valid_operand(self, other):
        return (hasattr(other, "lastname") and
                hasattr(other, "firstname"))
    def __eq__(self, other):
        if not self._is_valid_operand(other):
            return NotImplemented
        return ((self.lastname.lower(), self.firstname.lower()) ==
                (other.lastname.lower(), other.firstname.lower()))
    def __lt__(self, other):
        if not self._is_valid_operand(other):
            return NotImplemented
        return ((self.lastname.lower(), self.firstname.lower()) <
                (other.lastname.lower(), other.firstname.lower()))
```

[🔼](#functools-documentation)
## Methods

[🔼](#functools-documentation)
## cmp to key

```python
functools.cmp_to_key(func)
```

Transform an old-style comparison function to a key function. 
Used with tools that accept key functions (such as sorted(), min(), max(), heapq.nlargest(), heapq.nsmallest(), itertools.groupby()). 
This function is primarily used as a transition tool for programs being converted from Python 2 which supported the use of comparison functions.

A comparison function is any callable that accepts two arguments, compares them, and returns a negative number for less-than, zero for equality, or a positive number for greater-than. 
A key function is a callable that accepts one argument and returns another value to be used as the sort key.

```python
sorted(iterable, key=cmp_to_key(locale.strcoll))  # locale-aware sort order
```

[🔼](#functools-documentation)
## partial

```python
functools.partial(func, /, *args, **keywords)
```

The partial() is used for partial function application which “freezes” some portion of a function’s arguments and/or keywords resulting in a new object with a simplified signature. 
For example, partial() can be used to create a callable that behaves like the int() function where the base argument defaults to two:

```python
>>> from functools import partial
>>> basetwo = partial(int, base=2)
>>> basetwo.__doc__ = 'Convert base 2 string to an int.'
>>> basetwo('10010')
18
```

[🔼](#functools-documentation)
## partialmethod

```python
class functools.partialmethod(func, /, *args, **keywords)
```

Return a new partialmethod descriptor which behaves like partial except that it is designed to be used as a method definition rather than being directly callable.

func must be a descriptor or a callable (objects which are both, like normal functions, are handled as descriptors).

When func is a descriptor (such as a normal Python function, classmethod(), staticmethod(), abstractmethod() or another instance of partialmethod), 
calls to __get__ are delegated to the underlying descriptor, and an appropriate partial object returned as the result.

When func is a non-descriptor callable, an appropriate bound method is created dynamically. This behaves like a normal Python function when used as a method: 
the self argument will be inserted as the first positional argument, even before the args and keywords supplied to the partialmethod constructor.

```python
class Cell:
    def __init__(self):
        self._alive = False
    @property
    def alive(self):
        return self._alive
    def set_state(self, state):
        self._alive = bool(state)
    set_alive = partialmethod(set_state, True)
    set_dead = partialmethod(set_state, False)

c = Cell()
c.alive
False
c.set_alive()
c.alive
True
```

[🔼](#functools-documentation)
## reduce

```python
functools.reduce(function, iterable, [initial, ]/)
```

Apply function of two arguments cumulatively to the items of iterable, from left to right, so as to reduce the iterable to a single value. 
For example, reduce(lambda x, y: x+y, [1, 2, 3, 4, 5]) calculates ((((1+2)+3)+4)+5). 
The left argument, x, is the accumulated value and the right argument, y, is the update value from the iterable. 
If the optional initial is present, it is placed before the items of the iterable in the calculation, and serves as a default when the iterable is empty. 
If initial is not given and iterable contains only one item, the first item is returned.

As opposed to accumulate() will only return the single final value. use when you only care about the final value. Use accumulate() when you care about the intermediate values.
