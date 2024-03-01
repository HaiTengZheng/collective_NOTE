# endian
- little-endian     the least significant byte is written to memory firt
- big-endian        the most significant byte is written to memory firt
```c
int a = 0x1245A78F
/* little-endian 
 * address              content
 * 0x...01              0x8F
 * 0x...02              0xA7
 * 0x...03              0x45
 * 0x...04              0x12
 */

/* big-endian 
 * address              content
 * 0x...01              0x12
 * 0x...02              0x45
 * 0x...03              0xA7
 * 0x...04              0x8F
 */
```
