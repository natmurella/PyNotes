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
        - [ceil](#ceil)
        - [floor](#floor)
        - [fabs](#fabs)
        - [fma](#fma)
        - [fmod](#fmod)
        - [modf](#modf)
        - [remainder](#remainder)
        - [trunc](#trunc)
    - [Floating Point Manipulation Functions](#floating-point-manipulation-functions)
        - [copysign](#copysign)
        - [frexp](#frexp)
        - [ldexp](#ldexp)
        - [isclose](#isclose)
        - [isfinite](#isfinite)
        - [isinf](#isinf)
        - [isnan](#isnan)
        - [nextafter](#nextafter)
        - [ulp](#ulp)
    - [Power, Exponential, and Logarithmic Functions](#power-exponential-and-logarithmic-functions)
        - [pow](#pow)
        - [sqrt](#sqrt)
        - [cbrt](#cbrt)
        - [exp](#exp)
        - [exp2](#exp2)
        - [expm1](#expm1)
        - [log](#log)
        - [log1p](#log1p)
        - [log2](#log2)
        - [log10](#log10)
    - [Summation and Product Functions](#summation-and-product-functions)
        - [dist](#dist)
        - [fsum](#fsum)
        - [hypot](#hypot)
        - [prod](#prod)
        - [sumprod](#sumprod)
    - [Angular Conversion](#angular-conversion)
        - [degrees](#degrees)
        - [radians](#radians)
    - [Trigonometric Functions](#trigonometric-functions)
        - [acos](#acos)
        - [asin](#asin)
        - [atan](#atan)
        - [atan2](#atan2)
        - [cos](#cos)
        - [sin](#sin)
        - [tan](#tan)
    - [Hyperbolic Functions](#hyperbolic-functions)
        - [acosh](#acosh)
        - [asinh](#asinh)
        - [atanh](#atanh)
        - [cosh](#cosh)
        - [sinh](#sinh)
        - [tanh](#tanh)
    - [Special Functions](#special-functions)
        - [erf](#erf)
        - [erfc](#erfc)
        - [gamma](#gamma)
        - [lgamma](#lgamma)
- [Constants](#constants)
    - [pi](#pi)
    - [e](#e)
    - [tau](#tau)
    - [inf](#inf)
    - [nan](#nan)

[🔼](#math-documentation)
## Methods

[🔼](#math-documentation)
### Number-Theoretic Functions

[🔼](#math-documentation)
#### comb

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
#### perm

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
#### factorial

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
#### gcd

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
#### lcm

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
#### isqrt

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
### Floating Point Arithmetic

[🔼](#math-documentation)
#### ceil

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
#### floor

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
#### fabs

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
#### fma

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
#### fmod

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
#### modf

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
#### remainder

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
#### trunc

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
### Floating Point Manipulation Functions

[🔼](#math-documentation)
#### copysign

```python
float = math.copysign(x, y)
```

Return a float with the magnitude (absolute value) of x but the sign of y. On platforms that support signed zeros, copysign(1.0, -0.0) returns -1.0.

```python
>>> math.copysign(3.14, -2.71)
-3.14
>>> math.copysign(-3.14, 2.71)
3.14
>>> math.copysign(3.14, -0.0)
-3.14
```

[🔼](#math-documentation)
#### frexp

```python
tuple = math.frexp(x)
```

Return the mantissa and exponent of x as the pair (m, e). m is a float and e is an integer such that x == m * 2**e exactly. 
If x is zero, returns (0.0, 0), otherwise 0.5 <= abs(m) < 1. This is used to “pick apart” the internal representation of a float in a portable way.

Note that frexp() has a different call/return pattern than its C equivalents: it takes a single argument and return a pair of values, 
rather than returning its second return value through an ‘output parameter’ (there is no such thing in Python).

```python
>>> math.frexp(3.14)
(0.785, 2)
>>> math.frexp(-3.14)
(-0.785, 2)
>>> math.frexp(2.678)
(0.8395, 2)
```

[🔼](#math-documentation)
#### ldexp

```python
float = math.ldexp(m, e)
```
Return x * (2**i). This is essentially the inverse of function frexp().

```python
>>> math.ldexp(0.785, 2)
3.14
>>> math.ldexp(-0.785, 2)
-3.14
>>> math.ldexp(0.8395, 2)
3.358
```

[🔼](#math-documentation)
#### isclose

```python
bool = math.isclose(a, b, *, rel_tol=1e-09, abs_tol=0.0)
```

Return True if the values a and b are close to each other and False otherwise.

Whether or not two values are considered close is determined according to given absolute and relative tolerances. 
If no errors occur, the result will be: abs(a-b) <= max(rel_tol * max(abs(a), abs(b)), abs_tol).

rel_tol is the relative tolerance – it is the maximum allowed difference between a and b, relative to the larger absolute value of a or b. 
For example, to set a tolerance of 5%, pass rel_tol=0.05. The default tolerance is 1e-09, which assures that the two values are the same within about 9 decimal digits. 
rel_tol must be nonnegative and less than 1.0.

abs_tol is the absolute tolerance; it defaults to 0.0 and it must be nonnegative. When comparing x to 0.0, 
isclose(x, 0) is computed as abs(x) <= rel_tol  * abs(x), which is False for any x and rel_tol less than 1.0. 
So add an appropriate positive abs_tol argument to the call.

The IEEE 754 special values of NaN, inf, and -inf will be handled according to IEEE rules. Specifically, NaN is not considered close to any other value, including NaN. 
inf and -inf are only considered close to themselves.

```python
>>> math.isclose(3.14, 3.14)
True
>>> math.isclose(3.14, 3.15)
False
>>> math.isclose(3.14, 3.15, rel_tol=0.01)
True
>>> math.isclose(3.14, 3.15, rel_tol=0.01, abs_tol=0.01)
True
```

[🔼](#math-documentation)
#### isfinite

```python
bool = math.isfinite(x)
```

Return True if x is neither an infinity nor a NaN, and False otherwise. (Note that 0.0 is considered finite.)

```python
>>> math.isfinite(3.14)
True
>>> math.isfinite(float('inf'))
False
>>> math.isfinite(float('nan'))
False
```

[🔼](#math-documentation)
#### isinf

```python
bool = math.isinf(x)
```

Return True if x is a positive or negative infinity, and False otherwise.

```python
>>> math.isinf(3.14)
False
>>> math.isinf(float('inf'))
True
```

[🔼](#math-documentation)
#### isnan

```python
bool = math.isnan(x)
```

Return True if x is a NaN (not a number), and False otherwise.

```python
>>> math.isnan(3.14)
False
>>> math.isnan(float('nan'))
True
```


[🔼](#math-documentation)
#### nextafter

```python
float = math.nextafter(x, y)
```

Return the floating-point value steps steps after x towards y.

If x is equal to y, return y, unless steps is zero.

```python
>>> math.nextafter(3.14, 2.71)
3.1399999999999997
>>> math.nextafter(3.14, 3.14)
3.14
>>> math.nextafter(3.14, 3.14, steps=0)
3.14
```

[🔼](#math-documentation)
#### ulp

```python
float = math.ulp(x)
```
Return the value of the least significant bit of the float x:
- If x is a NaN (not a number), return x.
- If x is negative, return ulp(-x).
- If x is a positive infinity, return x.
- If x is equal to zero, return the smallest positive denormalized representable float (smaller than the minimum positive normalized float, sys.float_info.min).
- If x is equal to the largest positive representable float, return the value of the least significant bit of x, such that the first float smaller than x is x - ulp(x).
- Otherwise (x is a positive finite number), return the value of the least significant bit of x, such that the first float bigger than x is x + ulp(x).
ULP stands for “Unit in the Last Place”.

```python
>>> math.ulp(3.14)
1.4210854715202004e-14
>>> math.ulp(0.0)
5e-324
>>> math.ulp(float('inf'))
inf
```



[🔼](#math-documentation)
### Power, Exponential, and Logarithmic Functions

[🔼](#math-documentation)
#### pow

```python
float = math.pow(x, y)
```

Return x raised to the power y. Exceptional cases follow Annex ‘F’ of the C99 standard as far as possible. In particular, pow(1.0, x) and pow(x, 0.0) always return 1.0, even when x is a zero or a NaN. If both x and y are finite, x is negative, and y is not an integer then pow(x, y) is undefined, and raises ValueError.

```python
>>> math.pow(2, 3)
8.0
>>> math.pow(2, 0)
1.0
>>> math.pow(2, 0.5)
1.4142135623730951
```

[🔼](#math-documentation)
#### sqrt

```python
float = math.sqrt(x)
```

Return the square root of x. If x is negative, raise ValueError.

```python
>>> math.sqrt(4)
2.0
>>> math.sqrt(9)
3.0
>>> math.sqrt(16)
4.0
```

[🔼](#math-documentation)
#### cbrt

```python
float = math.cbrt(x)
```

Return the cube root of x.

```python
>>> math.cbrt(27)
3.0
>>> math.cbrt(64)
4.0
>>> math.cbrt(125)
5.0
```

[🔼](#math-documentation)
#### exp

```python
float = math.exp(x)
```

Return e raised to the power of x, where e is the base of natural logarithms.

```python
>>> math.exp(0)
1.0
>>> math.exp(1)
2.718281828459045
>>> math.exp(2)
7.3890560989306495
```

[🔼](#math-documentation)
#### exp2

```python
float = math.exp2(x)
```

Return 2 raised to the power of x.

```python
>>> math.exp2(0)
1.0
>>> math.exp2(1)
2.0
>>> math.exp2(2)
4.0
```

[🔼](#math-documentation)
#### expm1

```python
float = math.expm1(x)
```

Return e raised to the power of x, minus 1. Here e is the base of natural logarithms.

```python
>>> math.expm1(0)
0.0
>>> math.expm1(1)
1.718281828459045
>>> math.expm1(2)
6.38905609893065
```

[🔼](#math-documentation)
#### log

```python
float = math.log(x, base=e)
```

Return the natural logarithm of x (to base e). If x is less than 0, raise ValueError. If x is 0, return negative infinity. If x is positive, return the natural logarithm of x.

```python
>>> math.log(1)
0.0
>>> math.log(2)
0.6931471805599453
>>> math.log(10)
2.302585092994046
```

[🔼](#math-documentation)
#### log1p

```python
float = math.log1p(x)
```

Return the natural logarithm of 1 + x (base e). The result is computed in a way which is accurate for x near zero.

```python
>>> math.log1p(0)
0.0
>>> math.log1p(1)
0.6931471805599453
>>> math.log1p(2)
1.0986122886681098
```

[🔼](#math-documentation)
#### log2

```python
float = math.log2(x)
```

Return the base-2 logarithm of x. This is usually more accurate than log(x, 2).

```python
>>> math.log2(1)
0.0
>>> math.log2(2)
1.0
>>> math.log2(8)
3.0
```

[🔼](#math-documentation)
#### log10

```python
float = math.log10(x)
```

Return the base-10 logarithm of x. This is usually more accurate than log(x, 10).

```python
>>> math.log10(1)
0.0
>>> math.log10(10)
1.0
>>> math.log10(100)
2.0
```




[🔼](#math-documentation)
### Summation and Product Functions

[🔼](#math-documentation)
#### dist

```python
float = math.dist(p, q)
```

Return the Euclidean distance between two points p and q, each given as a sequence (or iterable) of coordinates. The two points must have the same dimension.

```python
>>> math.dist([0, 0], [1, 1])
1.4142135623730951
>>> math.dist([0, 0, 0], [1, 1, 1])
1.7320508075688772
```

[🔼](#math-documentation)
#### fsum

```python
float = math.fsum(iterable)
```

Return an accurate floating point sum of values in the iterable. Avoids loss of precision by tracking multiple intermediate partial sums.

```python
>>> math.fsum([1.0, 2.0, 3.0, 4.0, 5.0])
15.0
```

[🔼](#math-documentation)
#### hypot

```python
float = math.hypot(x, y)
```

Return the Euclidean norm, sqrt(x*x + y*y). This is the length of the vector from the origin to point (x, y).

```python
>>> math.hypot(3, 4)
5.0
>>> math.hypot(5, 12)
13.0
```

[🔼](#math-documentation)
#### prod

```python
float = math.prod(iterable, *, start=1)
```

Return the product of the numbers in the iterable. The default start value for the product is 1.

```python
>>> math.prod([1, 2, 3, 4, 5])
120
>>> math.prod([1, 2, 3, 4, 5], start=10)
1200
```

[🔼](#math-documentation)
#### sumprod

```python
float = math.sumprod(iterable)
```

Return the sum of products of values from two iterables p and q.

Raises ValueError if the inputs do not have the same length.

Roughly equivalent to:

sum(itertools.starmap(operator.mul, zip(p, q, strict=True)))
For float and mixed int/float inputs, the intermediate products and sums are computed with extended precision.

```python
>>> a = [1, 2, 3]
>>> b = [4, 5, 6]
>>> math.sumprod(a, b)
32
```


[🔼](#math-documentation)
### Angular Conversion

[🔼](#math-documentation)
#### degrees

```python
float = math.degrees(x)
```

Convert angle x from radians to degrees.

```python
>>> math.degrees(math.pi)
180.0
>>> math.degrees(math.pi / 2)
90.0
>>> math.degrees(math.pi / 4)
45.0
```

[🔼](#math-documentation)
#### radians

```python
float = math.radians(x)
```

Convert angle x from degrees to radians.

```python
>>> math.radians(180)
3.141592653589793
>>> math.radians(90)
1.5707963267948966
>>> math.radians(45)
0.7853981633974483
```


[🔼](#math-documentation)
### Trigonometric Functions

[🔼](#math-documentation)
#### acos

```python
float = math.acos(x)
```

Return the arc cosine of x, in radians. The result is between 0 and π.

```python
>>> math.acos(1)
0.0
>>> math.acos(0)
1.5707963267948966
>>> math.acos(-1)
3.141592653589793
```

[🔼](#math-documentation)
#### asin

```python
float = math.asin(x)
```

Return the arc sine of x, in radians. The result is between -π/2 and π/2.

```python
>>> math.asin(1)
1.5707963267948966
>>> math.asin(0)
0.0
>>> math.asin(-1)
-1.5707963267948966
```

[🔼](#math-documentation)
#### atan

```python
float = math.atan(x)
```

Return the arc tangent of x, in radians. The result is between -π/2 and π/2.

```python
>>> math.atan(0)
0.0
>>> math.atan(1)
0.7853981633974483
>>> math.atan(-1)
-0.7853981633974483
```

[🔼](#math-documentation)
#### atan2

```python
float = math.atan2(y, x)
```

Return the arc tangent of y / x, in radians. The result is between -π and π. The vector in the plane from the origin to point (x, y) makes this angle with the positive X axis. The point of atan2() is that the signs of both inputs are known to it, so it can compute the correct quadrant for the angle. For example, atan(1) and atan2(1, 1) are both π/4, but atan2(-1, -1) is -3π/4.

```python
>>> math.atan2(0, 1)
0.0
>>> math.atan2(1, 1)
0.7853981633974483
>>> math.atan2(-1, -1)
-2.356194490192345
```

[🔼](#math-documentation)
#### cos

```python
float = math.cos(x)
```

Return the cosine of x radians.

```python
>>> math.cos(0)
1.0
>>> math.cos(math.pi)
-1.0
>>> math.cos(math.pi / 2)
6.123233995736766e-17
```

[🔼](#math-documentation)
#### sin

```python
float = math.sin(x)
```

Return the sine of x radians.

```python
>>> math.sin(0)
0.0
>>> math.sin(math.pi)
1.2246467991473532e-16
>>> math.sin(math.pi / 2)
1.0
```

[🔼](#math-documentation)
#### tan

```python
float = math.tan(x)
```

Return the tangent of x radians.

```python
>>> math.tan(0)
0.0
>>> math.tan(math.pi)
-1.2246467991473532e-16
>>> math.tan(math.pi / 4)
0.9999999999999999
```


[🔼](#math-documentation)
### Hyperbolic Functions

[🔼](#math-documentation)
#### acosh

```python
float = math.acosh(x)
```

[🔼](#math-documentation)
#### asinh

```python
float = math.asinh(x)
```

[🔼](#math-documentation)
#### atanh

```python
float = math.atanh(x)
```

[🔼](#math-documentation)
#### cosh

```python
float = math.cosh(x)
```

[🔼](#math-documentation)
#### sinh

```python
float = math.sinh(x)
```

[🔼](#math-documentation)
#### tanh

```python
float = math.tanh(x)
```

[🔼](#math-documentation)
### Special Functions

[🔼](#math-documentation)
#### erf

```python
float = math.erf(x)
```

Return the error function at x. The error function is defined as 2/sqrt(π) times the integral of exp(-t**2) from 0 to x.

[🔼](#math-documentation)
#### erfc

```python
float = math.erfc(x)
```

Return the complementary error function at x. The complementary error function is defined as 2/sqrt(π) times the integral of exp(-t**2) from x to infinity.

[🔼](#math-documentation)
#### gamma

```python
float = math.gamma(x)
```

[🔼](#math-documentation)
#### lgamma

```python
float = math.lgamma(x)
```




[🔼](#math-documentation)
## Constants

[🔼](#math-documentation)
### pi

```python
float = math.pi
```

The mathematical constant π = 3.141592653589793.

[🔼](#math-documentation)
#### e

```python
float = math.e
```

The mathematical constant e = 2.718281828459045.

[🔼](#math-documentation)
#### tau

```python
float = math.tau
```

The mathematical constant τ = 6.283185307179586. Tau is a circle constant equal to 2π, the ratio of a circle’s circumference to its radius. To learn more about Tau, check out Vi Hart’s video Pi is (still) Wrong.

[🔼](#math-documentation)
#### inf

```python
float = math.inf
```

A floating-point positive infinity. (For negative infinity, use -math.inf.) Equivalent to the output of float('inf').

[🔼](#math-documentation)
#### nan

```python
float = math.nan
```

A floating-point “not a number” (NaN) value. Equivalent to the output of float('nan').

