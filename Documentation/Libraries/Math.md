# Math Documentation
[⬅](../../README.md)

## Contents
- [Methods](#methods)
    - [Number-Theoretic Functions](#number-theoretic-functions)
        - [comb](#comb)
        - [perm](#perm)
        - [factorial](#factorial)
        - [gcd](#gcd)
        - [lcm](#lcm)
        - [isqrt](#isqrt)
    - [Floating Point Arithmetic](#floating-point-arithmetic)
    - [Floating Point Manipulation Functions](#floating-point-manipulation-functions)
    - [Power, Exponential, and Logarithmic Functions](#power-exponential-and-logarithmic-functions)
    - [Summation and Product Functions](#summation-and-product-functions)
    - [Angular Conversion](#angular-conversion)
    - [Trigonometric Functions](#trigonometric-functions)
    - [Hyperbolic Functions](#hyperbolic-functions)
- [Constants](#constants)

[🔼](#math-documentation)
## Methods

[🔼](#math-documentation)
### comb

```python
int = math.comb(n, k)
```

Return the number of ways to choose k items from n items without repetition and without order.

Evaluates to n! / (k! * (n - k)!) when k <= n and evaluates to zero when k > n.

Also called the binomial coefficient because it is equivalent to the coefficient of k-th term in polynomial expansion of (1 + x)ⁿ.

Raises TypeError if either of the arguments are not integers. Raises ValueError if either of the arguments are negative.

```python
>>> math.comb(3, 1)
3
>>> math.comb(3, 2)
3
>>> math.comb(3, 3)
1
>>> math.comb(3, 4)
0
```

[🔼](#math-documentation)
### perm

```python
int = math.perm(n, k)
```

Return the number of ways to choose k items from n items without repetition and with order. (order matters!) ([1, 2] != [2, 1])

Evaluates to n! / (n - k)! when k <= n and evaluates to zero when k > n.

If k is not specified or is None, then k defaults to n and the function returns n!.

Raises TypeError if either of the arguments are not integers. Raises ValueError if either of the arguments are negative.

```python
>>> math.perm(3, 1)
3
>>> math.perm(3, 2)
6
>>> math.perm(3, 3)
6
>>> math.perm(3, 4)
0
```

[🔼](#math-documentation)
### factorial

```python
int = math.factorial(n)
```

Return n factorial as an integer. Raises ValueError if n is not integral or is negative.

```python
>>> math.factorial(3)
6
>>> math.factorial(0)
1
>>> math.factorial(5)
120
```

[🔼](#math-documentation)
### gcd

```python
int = math.gcd(*integers)
```

Return the greatest common divisor of the specified integer arguments. 
If any of the arguments is nonzero, then the returned value is the largest positive integer that is a divisor of all arguments. 
If all arguments are zero, then the returned value is 0. gcd() without arguments returns 0.

```python
>>> math.gcd(24, 36)
12
>>> math.gcd(36, 24)
12
>>> math.gcd(94, 87)
1
```

[🔼](#math-documentation)
### lcm

```python
int = math.lcm(*integers)
```

The least common multiple of two numbers is the smallest positive integer that is evenly divisible by both numbers.

Return the least common multiple of the specified integer arguments. If all arguments are nonzero, 
then the returned value is the smallest positive integer that is a multiple of all arguments. 
If any of the arguments is zero, then the returned value is 0. lcm() without arguments returns 1.

```python
>>> math.lcm(24, 36)
72
>>> math.lcm(6, 11)
66
>>> math.lcm(0, 11)
0
```

[🔼](#math-documentation)
### isqrt

```python
int = math.isqrt(n)
```

Return the integer square root of the nonnegative integer n. 
This is the floor of the exact square root of n, or equivalently the greatest integer a such that a² ≤ n.

For some applications, it may be more convenient to have the least integer a such that n ≤ a², 
or in other words the ceiling of the exact square root of n. For positive n, this can be computed using a = 1 + isqrt(n - 1).

```python
>>> math.isqrt(10)
3
>>> math.isqrt(16)
4
>>> math.isqrt(25)
5
```






[🔼](#math-documentation)
### Number-Theoretic Functions

[🔼](#math-documentation)
### ceil

```python
int = math.ceil(x)
```

Return the ceiling of x, the smallest integer greater than or equal to x. If x is not a float, delegates to x.__ceil__, which should return an Integral value.

```python
>>> math.ceil(3.14)
4
>>> math.ceil(3.0)
3
>>> math.ceil(-3.14)
-3
>>> math.ceil(-3.0)
-3
```

[🔼](#math-documentation)
### floor

```python
int = math.floor(x)
```

Return the floor of x, the largest integer less than or equal to x. If x is not a float, delegates to x.__floor__, which should return an Integral value.

```python
>>> math.floor(3.14)
3
>>> math.floor(3.0)
3
>>> math.floor(-3.14)
-4
>>> math.floor(-3.0)
-3
```

[🔼](#math-documentation)
### fabs

```python
float = math.fabs(x)
```

Return the absolute value of x.

```python
>>> math.fabs(3.14)
3.14
>>> math.fabs(-3.14)
3.14
>>> math.fabs(0.0)
0.0
```

[🔼](#math-documentation)
### fma

```python
float = math.fma(x, y, z)
```

Fused multiply-add operation. Return (x * y) + z, computed as though with infinite precision and range followed by a single round to the float format. 
This operation often provides better accuracy than the direct expression (x * y) + z.

This function follows the specification of the fusedMultiplyAdd operation described in the IEEE 754 standard. 
The standard leaves one case implementation-defined, namely the result of fma(0, inf, nan) and fma(inf, 0, nan). 
In these cases, math.fma returns a NaN, and does not raise any exception.

```python
>>> math.fma(3.14, 2.71, 1.0)
10.7594
```

[🔼](#math-documentation)
### fmod

```python
float = math.fmod(x, y)
```

Return the floating-point remainder of x / y, as defined by the platform C library function fmod(x, y). 
Note that the Python expression x % y may not return the same result. The intent of the C standard is that fmod(x, y) be exactly (mathematically; 
to infinite precision) equal to x - n*y for some integer n such that the result has the same sign as x and magnitude less than abs(y). 
Python’s x % y returns a result with the sign of y instead, and may not be exactly computable for float arguments. 
For example, fmod(-1e-100, 1e100) is -1e-100, but the result of Python’s -1e-100 % 1e100 is 1e100-1e-100, 
which cannot be represented exactly as a float, and rounds to the surprising 1e100. For this reason, function fmod() 
is generally preferred when working with floats, while Python’s x % y is preferred when working with integers.

```python
>>> math.fmod(3.14, 2.71)
0.43
```

[🔼](#math-documentation)
### modf

```python
tuple = math.modf(x)
```

Return the fractional and integer parts of x. Both results carry the sign of x and are floats.

Note that modf() has a different call/return pattern than its C equivalents: it takes a single argument and return a pair of values, rather than returning its second return value through an ‘output parameter’ (there is no such thing in Python).

```python
>>> math.modf(3.14)
(0.14, 3.0)
>>> math.modf(-3.14)
(-0.14, -3.0)
>>> math.modf(2.678)
(0.678, 2.0)
```

[🔼](#math-documentation)
### remainder

```python
float = math.remainder(x, y)
```

Return the IEEE 754-style remainder of x with respect to y. For finite x and finite nonzero y, this is the difference x - n*y, where n is the closest integer to the exact value of the quotient x / y. If x / y is exactly halfway between two consecutive integers, the nearest even integer is used for n. The remainder r = remainder(x, y) thus always satisfies abs(r) <= 0.5 * abs(y).

Special cases follow IEEE 754: in particular, remainder(x, math.inf) is x for any finite x, and remainder(x, 0) and remainder(math.inf, x) raise ValueError for any non-NaN x. If the result of the remainder operation is zero, that zero will have the same sign as x.

On platforms using IEEE 754 binary floating point, the result of this operation is always exactly representable: no rounding error is introduced.

```python
>>> math.remainder(3.14, 2.71)
0.43
```

[🔼](#math-documentation)
### trunc

```python
int = math.trunc(x)
```

Return x with the fractional part removed, leaving the integer part. This rounds toward 0: trunc() is equivalent to floor() for positive x, and equivalent to ceil() for negative x. If x is not a float, delegates to x.__trunc__, which should return an Integral value.

```python
>>> math.trunc(3.14)
3
>>> math.trunc(-3.14)
-3
>>> math.trunc(3.0)
3
>>> math.trunc(-3.0)
-3
```



[🔼](#math-documentation)
### Floating Point Arithmetic

[🔼](#math-documentation)
### Floating Point Manipulation Functions

[🔼](#math-documentation)
### Power, Exponential, and Logarithmic Functions

[🔼](#math-documentation)
### Summation and Product Functions

[🔼](#math-documentation)
### Angular Conversion

[🔼](#math-documentation)
### Trigonometric Functions

[🔼](#math-documentation)
### Hyperbolic Functions

[🔼](#math-documentation)
## Constants
