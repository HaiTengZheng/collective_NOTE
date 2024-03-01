# the memory-management APIs
- malloc(3)
- calloc
- realloc
- free

# malloc(3)
a library API
> man 3 malloc
```c
void *malloc(size_t size);
/* size_t : [0, SIZE_MAX], typedef - long unsigned int on 64-bit linux,
 *          typedef - unsigned int on 32-bit linux
 */
```
- The content of the memory chunk allocated by malloc(3) is considerrd to be
  random, it's the programmer's responsibility to initialize the memory before
  the readling from it, if you fail to do so, it result in a bug called
  `Uninitialized Memory Read (UMR)`.
- Need larger alignment values -> `posix_memalign(3)` API. Deallocate its memory 
  as usual `free(3)`.
- how much memory can malloc allocated with a single call? 
  -> 8EB (theoretical answer)
- malloc will result NULL, or, a non-NULL pointer that can be passed to free,
  even if the pointer is non-NULL, there is no memory, so don't use malloc(0)
