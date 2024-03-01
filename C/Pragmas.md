# `#pragma`
> https://gcc.gnu.org/onlinedocs/cpp/Pragmas.html
The directive is the method specified by the C standard for providing additional
information to the compiler.
- The forms of this directive specified by C standard are prefixed with `STDC`,
  GNU-defined with `GCC`
```c
#pragma once
/* non-standard, cause the current source file to be included only once in a
 * single compilation
 */
```

# `_Pragma` 
C99 introduce the `_Pragma` operator, address the problem(`#pragma` as a 
directive, can't be produced as the result of macro expansion).
- can be embedded in a macro
```c
_Pragma 
```

