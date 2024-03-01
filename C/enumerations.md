# enumerations
a custom data type used for storing constant integer values and referring to 
    them by names
## type
C89
- default value type : signed int
- GCC compiler option : -fshort-enums   (instead use the smallest integer type)
(don't mix the use of these options in the same program)

# define enumerations
keyword : `enum`
name : (optional)
list : a list of constant names (separated by commas and enclosed in braces)
variables : (optional) (you can't define it if don't named)
ending : a semicolon
```c
enum fruit_name {apple = -17, cherry, peach = cherry - 6} my_fruit;
/* apple = -17, cherry = -16, peach = -10
 * you can refer to an enumerations value defined earlier in the same 
 * enumerations 
 * you can't change the values in an enumerations once it has been defined
 */
```
