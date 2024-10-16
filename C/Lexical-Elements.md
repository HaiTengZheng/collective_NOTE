# Lexical Elements
The lexical elements that make up C source after preprocessing are called 
`tokens`.
- Keywords
- Identifiers
- Constants
- Operators
- Separators

# Identifier
Identifiers are sequences of characters used for naming variables, new data 
types, and preprocessor macros.
- Letters
- Decimal digits
- Underscore character `_`
> GNU Extensions: `$` the dollar sign can be included.

# Keywords
- ANSI C89
- ISO C99
- GNU Extensions
> `restrict` is recognized as a keyword.

# Constants
A constant is a literal numeric or character value.
## Integer Constants
An integer constant is a sequence of digits, with an optional prefix to denote
a number base.

- Hexadecimal (base 16): `0x` or `0X`
- Octal (base 8): If the first digit is 0 (zero), and the next character is not
    `x` or `X`.
- Decimal (base 10): Use digits from 0 to 10.

You can force an integer constant to  be of a long and/or unsigned integer type
by **appending** a sequence of one or more letters to the end of the constant.
- `u` or `U`: Unsigned integer type
- `l` or `L`: Long integer type
> ISO C99 and GNU Extensions: `LL` for **long long int**,`ULL` for 
    **unsigned long long int**
## Character Constants
A character constant is usually a single character enclosed within single
quotation marks. A character constant is of type **int** by default.

Escape sequence:
- \\
- \?
- \'
- \"
- \a
- \b
- \e (GNU Extensions: <ESC> character)
- \f
- \n
- \r
- t
- \v
- \o, \oo, \ooo
- \xh, \xhh, \xhhh, ...
To use any of these, enclose the sequence in single quotes, and treat it as if 
it were any other character, e.g., `'m'`.
## Raal Constants
A real number constant is a value that represents a fractional (floating point)
number.
> Real number constants can also be followed by `e` or `E`, and an Integer
    exponent.
## String constants
A string constant is a sequence of zero or more characters, digits, and escape
sequences enclosed within double quotation marks.
All string constants contain a null termination character `\0` as their last
character.
You can use a backslash `\` to break onto separate lines.

# Operators
An operator is a special token that performs an operation.

# Separators
A separator separates tokens.

# White Space
It is the collective term used for several characters:
- the space character
- the tab character
- the newline character
- the vertical tab character
- the form-feed character

It is not a token.

> Note: In string constants, spaces and tabs are **not** ignored, they are part
    of the string.
