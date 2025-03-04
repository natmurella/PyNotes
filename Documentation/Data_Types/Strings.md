[⬅](../../README.md)
# Strings Documentation
## Contents
- [Methods](#methods)
  - [Find](#find)
  - [Format](#format)
  - [Split](#split)
- [Common Usages](#common-usages)
  - [String to List](#string-to-list)

[🔼](#strings-documentation)
## Methods

[🔼](#strings-documentation)
### Find

```python
"str".find(substring: str, start: int = None, end: int = None)
```
Finds the first occruence of substring withing str and returns the index, else returns -1.
If start and/or end are included, it only looks within that slice.
Note: to check if a string contains a substring, better to use "in":
```python
if substring in my_sting:
```
Examples
```python
>>> "hello".find("e")
1
>>> "hello".find("ell", 3, 4)
-1
```

[🔼](#strings-documentation)
### Format

```python
"{}".format(*args, **kwargs)
f"{variable}"
```
Fills the "{}" in a string with arguments passed to format function.

Decimals:
```python
>>> "{:.2f}".format(0.1111) # rounding
"0.11"
>>> f"{0.1111:.2f}"
"0.11"
>>> "{:10.2f}".format(0.1111) # fixed width 10
"      0.11"
```
Padding and Alignement:
```python
>>> "{:05d}".format(42) # zero padding width 5
"00042"
>>> "{:>5d}".format(42) # width 5 push right
"   42"
>>> "{:<5d}".format(42) # width 5 push left
"42   "
>>> "{:^5d}".format(42) # width 5 centered
" 42  "
>>> "{:,}".format(1000000) # separator thousands with comma
"1,000,000"
>>> "{:_}".format(1000000) # separator thousands with _
"1_000_000"
```
Conversions:
```python
>>> "{:b}".format(42) # binary
"101010"
>>> "{:o}".format(42) # octal
"52"
>>> "{:x}".format(42) # hex lowercase
"2a"
>>> "{:X}".format(42) # hex uppercase
"2A"
>>> "{:.2%}".format(0.1234) # percentage
"12.34%"
>>> "{:.2e}".format(1234) # scientific notation
"1.23e+03"
```

[🔼](#strings-documentation)
### Split

```python
string.split(separator: str = " ", maxplit: int = -1)
```
Splits the string into a list of strings, splitting int the spearator (removing it).

[🔼](#strings-documentation)
## Common Usages

[🔼](#strings-documentation)
### String to List and Back

```python
letters = list(word)
word = "".join(letters)
```
