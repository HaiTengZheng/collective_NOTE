# complex types
C99
> <complex.h>
use `_Complex` or `complex`
## float _Complex
## double _Complex
## long double _Complex

# macros
## complex
expands to `_Complex`
e.g
> double complex
## I
a constant of type `const float _Complex` having the value of the imaginary
    unit normally referred to as `i`

# functions
## creal()
return the real part of a double complex number
## cimag()
return the imaginary part of a double complex number

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# GNU extensions for complex number types
GNU extensions to C89
GCC's extension allow for complex types other than floating-point, so that you
    can declare complex character types and complex integer types float float
`__complex__` can be used with any of the primitive data types,
    e.g. `__complex__ int`, both real and imaginary part are `int` data type
## __complex__ float
## __complex__ double
## __complex__ long double

# exact real part and imaginary part
real part : __real__
imaginary part : __imag__
```c
__complex__ float a = 4 + 3i

float b = __real__ a; /* b is now 4 */
float c = __imag__ a; /* c is now 3 */
```
