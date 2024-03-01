# real number types
> <float.h>
- all floating point data types are signed
- finite precision, most computer system that GCC compilers for use a binary
    representation for real numbers, which is unable to precisely represent
    numbers
## float
- FLT_MIN   (1e-37)
- FLT_MAX   (1e37)
## double
(at least as large as the float type)
- DBL_MIN   
- DBL_MAX   
## long double
(at least as large as the float type)
- LDBL_MIN
- LDBL_MAX

# binary number
using `0b` or `0B` prefix
```c
char ch = 0b01111110;
```
