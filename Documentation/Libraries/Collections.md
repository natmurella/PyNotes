[⬅](../../README.md)
# Collections Documentation
## Contents
- [Containers](#methods)
  - [Counter](#counter)
    - [Elements](#elements)
    - [Most Common](#most-common)
    - [Subtract](#subtract)
    - [Total](#total)
    - [Comparison Operations](#comparison-operations)
    - [Arithmetic Operations](#arithmetic-operations)

[🔼](#collections-documentation)
## Methods

[🔼](#collections-documentation)
### Counter

```python
class collections.Counter([iterable-or-mapping])
```
A counter tool is provided to support convenient and rapid tallies.
It is a collection where elements are stored as dictionary keys and their counts are stored as dictionary values. 
Counts are allowed to be any integer value including zero or negative counts. The Counter class is similar to bags or multisets in other languages.

Initialisaio:
```python
from collections import Counter 
# With sequence of items  
print(Counter(['B','B','A','B','C','A','B',
               'B','A','C']))
# with dictionary 
print(Counter({'A':3, 'B':5, 'C':2}))
# with keyword arguments 
print(Counter(A=3, B=5, C=2))
```

Counter objects have a dictionary interface except that they return a zero count for missing items instead of raising a KeyError:
```python
>>> c = Counter(['eggs', 'ham'])
>>> c['bacon']                              # count of a missing element is zero
0
```

[🔼](#collections-documentation)
#### Elements

```python
list = counter.elements()
```

Return an iterator over elements repeating each as many times as its count. 
Elements are returned in the order first encountered. If an element’s count is less than one, elements() will ignore it.

```python
>>> c = Counter(a=4, b=2, c=0, d=-2)
>>> sorted(c.elements())
['a', 'a', 'a', 'a', 'b', 'b']
```

[🔼](#collections-documentation)
#### Most Common

```python
list = counter.most_common([n])
```

Return a list of the n most common elements and their counts from the most common to the least. 
If n is omitted or None, most_common() returns all elements in the counter. 
Elements with equal counts are ordered in the order first encountered:

```python
>>> Counter('abracadabra').most_common(3)
[('a', 5), ('b', 2), ('r', 2)]
```

[🔼](#collections-documentation)
#### Subtract

```python
counter.subtract([iterable-or-mapping])
```

Elements are subtracted from an iterable or from another mapping (or counter). 
Like dict.update() but subtracts counts instead of replacing them. Both inputs and outputs may be zero or negative.

```python
>>> c = Counter(a=4, b=2, c=0, d=-2)
>>> d = Counter(a=1, b=2, c=3, d=4)
>>> c.subtract(d)
>>> c
Counter({'a': 3, 'b': 0, 'c': -3, 'd': -6})
```

[🔼](#collections-documentation)
#### Total

```python
int = counter.total()
```

Compute the sum of the counts.

```python
>>> c = Counter(a=10, b=5, c=0)
>>> c.total()
15
```

[🔼](#collections-documentation)
#### Comparison Operations

```python
# 1. Equality (==) and Inequality (!=)
# When comparing Counters, missing keys are treated as having a count of 0.
>>> c1 = Counter(a=1)
>>> c2 = Counter(a=1, b=0)
>>> c1 == c2
True
# 2. Subset and Superset Comparisons (<= and <, >= and >)
# The <= operator returns True if every count in the left Counter is less than or equal to the corresponding count in the right Counter.
>>> c4 = Counter(a=1, b=2)
>>> c5 = Counter(a=2, b=3, c=1)
>>> c4 <= c5
True
# If neither Counter is a subset of the other, both <= and >= comparisons will return False.
>>> c6 = Counter(a=2, b=3)
>>> c7 = Counter(a=3, c=1)
>>> c6 <= c7
False
```

[🔼](#collections-documentation)
#### Arithmetic Operations

```python
>>> c = Counter(a=3, b=1)
>>> d = Counter(a=1, b=2)
# 1. Addition (c + d)
>>> c + d
Counter({'a': 4, 'b': 3})
# 2. Subtraction (c - d) (negatives are dropped)
>>> c - d
Counter({'a': 2})
# 3. Intersection (c & d)
# The intersection takes the minimum of counts for each key: result[key] = min(c[key], d[key])
>>> c & d
Counter({'a': 1, 'b': 1})
# 4. Union (c | d)
# The union takes the maximum of counts for each key: result[key] = max(c[key], d[key])
>>> c | d
Counter({'a': 3, 'b': 2})
# 5. Unary Plus (+c)
# Returns a new Counter with negative (and zero) counts removed.
>>> c = Counter(a=3, b=-1)
>>> +c
Counter({'a': 3})
# 6. Unary Minus (-c)
# Returns a new Counter with all positive counts removed and negative counts turned positive.
>>> -c
Counter({'b': 1})
```






