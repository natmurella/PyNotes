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
  - [Deque](#deque)
    - [Append](#append)
    - [Appendleft](#appendleft)
    - [Clear](#clear)
    - [Copy](#copy)
    - [Count](#count)
    - [Extend](#extend)
    - [Extendleft](#extendleft)
    - [Index](#index)
    - [Insert](#insert)
    - [Pop](#pop)
    - [Popleft](#popleft)
    - [Remove](#remove)
    - [Reverse](#reverse)
    - [Rotate](#rotate)
    - [Additional Support](#additional-support)

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

[🔼](#collections-documentation)
### Deque

```python
class collections.deque([iterable[, maxlen]])
```
Returns a new deque object initialized left-to-right (using append()) with data from iterable. If iterable is not specified, the new deque is empty.
Deques are a generalization of stacks and queues (the name is pronounced “deck” and is short for “double-ended queue”). 
Deques support thread-safe, memory efficient appends and pops from either side of the deque with approximately the same O(1) performance in either direction.
Though list objects support similar operations, they are optimized for fast fixed-length operations and 
incur O(n) memory movement costs for pop(0) and insert(0, v) operations which change both the size and position of the underlying data representation.
If maxlen is not specified or is None, deques may grow to an arbitrary length. Otherwise, the deque is bounded to the specified maximum length. 
Once a bounded length deque is full, when new items are added, a corresponding number of items are discarded from the opposite end. 
Bounded length deques provide functionality similar to the tail filter in Unix. 
They are also useful for tracking transactions and other pools of data where only the most recent activity is of interest.

[🔼](#collections-documentation)
#### Append

```python
deque.append(x)
```

Add x to the right side of the deque.

```python
>>> d = deque([1, 2, 3])
>>> d.append(4)
>>> d
deque([1, 2, 3, 4])
```

[🔼](#collections-documentation)
#### Appendleft

```python
deque.appendleft(x)
```

Add x to the left side of the deque.

```python
>>> d = deque([1, 2, 3])
>>> d.appendleft(0)
>>> d
deque([0, 1, 2, 3])
```

[🔼](#collections-documentation)
#### Clear

```python
deque.clear()
```

Remove all elements from the deque leaving it with length 0.

```python
>>> d = deque([1, 2, 3])
>>> d.clear()
>>> d
deque([])
```

[🔼](#collections-documentation)
#### Copy

```python
deque.copy()
```

Create a shallow copy of the deque.

```python
>>> d = deque([1, 2, 3])
>>> d2 = d.copy()
>>> d2
deque([1, 2, 3])
```

[🔼](#collections-documentation)
#### Count

```python
deque.count()
```

Count the number of deque elements equal to x.

```python
>>> d = deque([1, 2, 3, 2, 1])
>>> d.count(2)
2
```

[🔼](#collections-documentation)
#### Extend

```python
deque.extend(iterable)
```

Extend the right side of the deque by appending elements from the iterable argument.

```python
>>> d = deque([1, 2, 3])
>>> d.extend([4, 5])
>>> d
deque([1, 2, 3, 4, 5])
```

[🔼](#collections-documentation)
#### Extendleft

```python
deque.extendleft(iterable)
```

Extend the left side of the deque by appending elements from iterable. 
Note, the series of left appends results in reversing the order of elements in the iterable argument.

```python
>>> d = deque([1, 2, 3])
>>> d.extendleft([4, 5])
>>> d
deque([5, 4, 1, 2, 3,])
```

[🔼](#collections-documentation)
#### Index

```python
idx = deque.index(x[, start[, stop]])
```

Return the position of x in the deque (at or after index start and before index stop). Returns the first match or raises ValueError if not found.

```python
>>> d = deque([1, 2, 3])
>>> d.index(2)
1
```

[🔼](#collections-documentation)
#### Insert

```python
deque.insert(i, x)
```

Insert x into the deque at position i. If the insertion would cause a bounded deque to grow beyond maxlen, an IndexError is raised.

```python
>>> d = deque([1, 2, 3])
>>> d.insert(1, 99)
>>> d
deque([1, 99, 3])
```

[🔼](#collections-documentation)
#### Pop

```python
x = deque.pop()
```

Remove and return an element from the right side of the deque. If no elements are present, raises an IndexError.

```python
>>> d = deque([1, 2, 3])
>>> d.pop()
3
>>> d
deque([1, 2])
```

[🔼](#collections-documentation)
#### Popleft

```python
x = deque.popleft()
```

Remove and return an element from the left side of the deque. If no elements are present, raises an IndexError.

```python
>>> d = deque([1, 2, 3])
>>> d.popleft()
3
>>> d
deque([2, 3])
```

[🔼](#collections-documentation)
#### Remove

```python
deque.remove(x)
```

Remove the first occurrence of value. If not found, raises a ValueError.

```python
>>> d = deque([1, 2, 3, 2])
>>> d.remove(2)
>>> d
deque([1, 3, 2])
```

[🔼](#collections-documentation)
#### Reverse

```python
deque.reverse(x)
```

Reverse the elements of the deque in-place and then return None.

```python
>>> d = deque([1, 2, 3])
>>> d.reverse()
>>> d
deque([3, 2, 1])
```

[🔼](#collections-documentation)
#### Rotate

```python
deque.rotate(n=1)
```

Rotate the deque n steps to the right. If n is negative, rotate to the left.
When the deque is not empty, rotating one step to the right is equivalent to d.appendleft(d.pop()), and rotating one step to the left is equivalent to d.append(d.popleft()).

```python
>>> d = deque([1, 2, 3, 4])
>>> d.rotate(2)
>>> d
deque([3, 4, 1, 2])
```

[🔼](#collections-documentation)
#### Additional Support

```python
d = deque([a, b, c])
# 1. Iteration
for item in d:
# 2. Length
len(d)
# 3. Reversed iterator
iterator = reversed(d)
# 4. Membership testing
if 12 in d:
# 5. Subscript References (Indexed access is O(1) at both ends but O(n) in the middle.)
d[0]
```





