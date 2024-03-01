#  Unicode
0 ~ 0x7f 与 ASCII 码点一一对应
0 ~ 0xff ISO/IEC 8859-1 (Latin-1) 

# UTF-8
- String
- str
```
0xxxxxxx                                // 0 ~ 0x7f
110xxxxx yyyyyyyy                       // 0x80 ~ 0x7ff
1110xxxx 10yyyyyy 10zzzzzz              // 0x800 ~ 0xfff
11110xxx 10yyyyyy 10zzzzzz 10wwwwww     // 0x10000 ~ 0x10ffff
```
## rules
1. Only the shortest encoding for any given code point is considered well-formed
2. Well-formed UTF-8 must not encode numbers from 0xd800 through 0xdfff or 
   beyond 0x10ffff

