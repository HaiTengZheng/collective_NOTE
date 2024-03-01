```c
#pragma comment(lib, "<import library name, full path, or relative path>");
// 在源代码中添加，来指定需要的库文件
// 优势-->设计师可以根据预处理指令来自定义需要链接哪些具体的库
#ifdef CUSTOMER_XYZ
#pragma comment(lib, "<cutomerXYZ-specific library>");
#else
#ifdef CUSTOMER_ABC
#pragma comment(lib, "<cutomerABC-specific library>");
#else
#ifdef CUSTOMER_MPQ
#pragma comment(lib, "<cutomerMPQ-specific library>");
#endif /* CUSTOMER_MPQ */
#endif /* CUSTOMER_ABC */
#endif /* CUSTOMER_XYZ */
```
