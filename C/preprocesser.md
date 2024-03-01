# preprocessor
- Preprocessor directives begin with `#`
- Only whitespace characters and comments delimited by /* and */ may appear
  before a preprocessor directive on a line.

# `#include`
```c
#include <filename>     /* standard library headers */
#include "filename"     /* search the same folder as the file appears in "" */
```

# `#define`
create
- symbolic constants
- macros
```c
#define identifier replacement-text
/* identifier should contain only uppercase letters and underscores */
/* constants */
#define PI 3.14
/* macros */
#define CIRCLE_AREA(x) ((PI) * (x) * (x)) /* this is an unsafe example */
#define RECTANGLE_AREA(x, y) ((x) * (y))
/* use backslash(\) continuation character at the end of the line to continue
 * the replacement-txt on the next line
 */
```

# `#undef`
undefine a symbolic constants or macros name

# conditional compilation
## `#if..#endif`
```c
#if !defined(MY_CONSTANT)
#define MY_CONSTANT 0
#endif
/* `#ifdef` is short for `#if define(name)` */
/* `#ifndef` is short for `#if !define(name)` */
/* `#elif` */
/* `#else` */

/* comment out blocks of code */
#if 0
    code prevented fromm compiling
#endif

/* debugging aid */
#define DEBUG
#ifdef DEBUG
    printf("Variable x = %d\n", x);
#endif
```

# `#error`
prints an implementation-dependent message, including the tokens specified in
the directive
```c
#error tokens
/* the tokens are sequences of characters separated by spaces */
#error 1 - Out of range error
```

# `#pragma`
causes an implementation-defined action
```c
#pragma tokens
/* A #pragma not recognized by the implementation is ignored */
```

# `#` and `##` operators
the `#` operator converts a replacement-text token to a string surrounded by
quotes
```c
#define HELLO(x) puts("Hello, " #x);
HELLO(John);
/* puts("Hello, " "John"); */
/* equal to puts("Hello, John"); */
```
the `##` operator concatenates two tokens
```c
#define TOCKENCONCAT(x, y) x ## y
TOCKENCONCAT(O, K);
/* Ok */
```

# `#line`
cause the subsequent source-code lines to be renumbered with the specified 
constant integer value
```c
#line 100
#line 100 "file.c"
```

# predefined symbolic constants
- __LINE__
- __FILE__
- __DATE__
- __TIME__
- __STDC__

# assertions
The `assert` macro defined in <assert.h> tests an expression's value at 
execution time. If the value is false(0), assert prints an error message and 
terminate the program by calling function `abort` of the general utilies library
(<stdlib.h>)
```c
assert(x <= 10);
/* if `#define NDEBUG` is defined, subsequent assertions in the source file are
 * ignored
 */
```
