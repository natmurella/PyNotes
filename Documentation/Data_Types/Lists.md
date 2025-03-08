# Lists Documentation
[⬅](../../README.md)

## Contents
- [Methods](#methods)
  - [Append](#append)
  - [Clear](#clear)
  - [Copy](#copy)
  - [Count](#count)
  - [Extend](#extend)
  - [Index](#index)
  - [Insert](#insert)
  - [Pop](#pop)
  - [Remove](#remove)
  - [Reverse](#reverse)
  - [Sort](#sort)
- [Common Usages](#common-usages)
  - [String to List](#string-to-list)
  - [List Length](#list-length)

[🔼](#lists-documentation)
## Methods

[🔼](#lists-documentation)
### Append

```python
list.append(element)
```
appends the element to the end of the list.

Examples
```python
>>> l = ["a", "b"]
>>> l.append("c")
>>> l
["a", "b", "c"]
```

[🔼](#lists-documentation)
### Extend

```python
list.extend(iterable)
```
Add the elements of the iterable at the end of the current list.

Example:
```python
>>> l = ["a", "b"]
>>> l.extend(["c", 1])
>>> l
["a", "b", "c", 1]
```

[🔼](#lists-documentation)
### Insert

```python
list.insert(pos, element)
list[pos] = element
```

[🔼](#lists-documentation)
### Pop

```python
elemt = list.pop(pos)
```
Removes the element at the specific position. returns the popped element.

[🔼](#lists-documentation)
### Remove

```python
list.remove(element)
```
Removesthe first element that matches from the list.

[🔼](#lists-documentation)
### Reverse

```python
list.reverse()
reversed_list = list[::-1]
```
reverses the order of elements, in place.

Example:
```python
>>> l = ["a", "b"]
>>> l.reverse()
>>> l
["b", "a"]
```

[🔼](#lists-documentation)
### Sort

```python
list.sort(reversed: bool = False, key: func = None)
```
Sorts the list in ascending order by default. Setting reverse to True will do descending order.

Example:
```python
>>> l = ["b", "a"]
>>> l.sort()
>>> l
["a", "b"]
```
```python
>>> l = [{"name": "david", "age": 45}, {"name": "mark", "age": 23}]
>>> l.sort(reversed=True, key=lambda x: x["age"])
>>> l
[{"name": "david", "age": 45}, {"name": "mark", "age": 23}]
```


[🔼](#lists-documentation)
## Common Usages
[🔼](#lists-documentation)
### String to List and Back
```python
letters = list(word)
word = "".join(letters)
```
[🔼](#lists-documentation)
### List Length
```python
>>> l = ["a", "b"]
>>> len(l)
2
```
