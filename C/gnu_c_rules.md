# 括号里的负荷语句可以看作表达式 (语句表达式)
可以出现在任何允许表达式的地方
```c
#define maxint(a, b)
    ({ int _a = (a), _b = (b); _a > _b ? _a : _b; })
/* 重新定义了 _a 和 _b，宏不会有副作用 */
```

# 零长度数组
定义变长对象的头结构
```c
struct var_data {
    int len;
    char data[0];
}
/* char data[0] 仅仅意味着程序中通过 var_data 结构体实例的 data[index] 成员
 * 可以访问 len 之后的第 index 个地址，它并没有为 data[] 数组分配内存，因此
 * sizeof(struct var_data) = sizeof(int)
 */
```

# 使用 1 个变量定义数组
```c
int
main(int argc, char *argv[])
{
    int i, n = argc;
    double x[n];

    for (i = 0; i < n; i++)
        x[i] = i;

    return 0;
}
```

# case 范围
```c
switch (ch) {
case '0' ... '9': c -= '0';
break;
case 'a' ... 'f': c -= 'a' - 10;
break
}
/* 注意：... 两边有空格
 * case '0' ... '3' 等价于
 * case '0': case '1': case '2': case '3':
 */

```

# typeof 关键字
typeof(x) 获得 x 的类型
```c
#define min(x, y) ({        \
const typeof(x) _x = (x);   \
const typeof(y) _y = (y);   \
(void) (&_x == &_y);        \
_x < _y ? _x : _y; })
/* (void) (&_x == &_y) 检查 _x 和 _y 的类型是否一致 */
```

# 可变参数宏
标准 C 支持可变参数函数，意味着函数的参数是不固定的。
GNU C 中宏也可以接受可变数目的参数
```c
#define pr_debug(fmt, arg...) \
    printk(fmgt, ##arg)

pr_debug("%s:%d", filename, line);
/* 扩展为 */ 
printk("%s:%d", filename, line);
/* ## 是为了处理 arg 不代表任何参数的情况，这时候前面的逗号就变得多余。
 * 使用 ## 之后，GNU C 预处理器会丢弃前面的逗号。
 */
pr_debug("success!\n")
/* 扩展为 */
printk("success!\n");
```

# 标号元素
GNU C 中，通过指定索引或结构体成员名，允许初始化值以任意顺序出现。
指定数组索引的方法是在初始化值前添加 "[INDEX]="，当然也可以用 "[FIRST ... LAST]"
的形式指定一个范围。
```c
unsigned char data[MAX] = { [0 ... MAX-1] = 0 };

/* 以标准 C 的形式初始化结构体 */
struct file_operations ext2_file_operations = {
    .llseek         = generic_file_llseek,
    .read           = generic_file_read;
    /* 这样可以通过索引或结构成名员来初始化，不必安装固定顺序 */
};
/* 可写成 */
struct file_operations ext2_file_operations = {
    llseek: generic_file_llseek,
    read: generic_file_read;
};
```

# 当前函数名
GNU C 预定义了两个标识符保持当前函数的名字
"__FUNCTION__" 保存函数在源码中的名字
"__PRETTY_FUNCTION__" 保存带语言特色的名字
C99 已经支持 "__func__" 宏，因此建议在 Linux 中不再使用 "__FUNCTION__"
```c
printf("This is function: %s", __func__);
```

# 特殊属性声明
GNU C 允许声明函数、变量和类型的特殊属性，以便手动优化代码和定制代码检查的方法。
要指定一个声明的属性，只需要在声明后添加 "__attribute__(( ATTRIBUTE ))"，其中
ATTRIBUTE 为属性说明，如果存在多个属性，则以逗号分隔。
## noreturn 
用于函数，表示该函数从不返回。这会让编译器优化代码，并消除不必要的警告信息
```c
#define ATTRIBUTE_NORET __attribute__((noreturn)) ....
asmlinkage NORET_TYPE void do_exit(long error_code) ATTRIB_NORET;
```
## format 
用于函数，表示该函数使用 printf, scanf 或 strftime 风格的参数，
指定 format 属性可以让编译器根据格式串检查参数类型
```c
asmlinkage int printk(const char *fmt, ...) 
    __attribute__ ((format (printf, 1, 2));
```
## unused
用于函数和变量，表示该函数或变量可能不会用到，这个函数可以避免编译器产生警告信息
## aligned
用于变量、结构体或联合体，指定变量、结构体或联合体的对齐方式，以字节为单位。
```c
struct example_struct {
    char a;
    int  b;
    long c;
} __attribute__ ((aligned(4)));
/* 表示该结构的类型变量为 4 */
```
## packed
用于变量和类型，用于变量或结构体成员时表示使用最小可能的对齐，用于枚举、结构体
或联合体类型时表示该类型使用最小的内存
```c
struct example_struct {
    char a;
    int  b;
    long c;
} __attribute__ ((packed(4)));
```

# 内建函数
通常以 __builtin 开始
## __builtin_return_address(LEVEL)
返回当前函数或其调用者的返回地址
LEVEL 指定调用栈的级数，0 表示当前函数的返回地址，1 表示当前函数的调用者的返回
    地址
## __builtin_constant_p(EXP)
用于判断一个值是否为编译时常数，EXP 为常数则函数返回 1，否则 0。
## __builtin_exepct(EXP, C)
用于为编译器体冬分支预测信息，其返回值是整数表达式 EXP 的值，C 的值必须是编译
时常数
```c
#define LIKELY(x) __builtin_expect(!!(x), 1)
#define UNLIKELY(x) __builtin_expect(!!(x), 0)
```

# do {} while (0)
主要用于宏定义
```c
#define SAFE_FREE(p) do { free(p); p = NULL;} while (0)
```

# goto
一般只限于错误处理中
```c
goto label;
label:
    something;
```
As a extension, GCC allows a goto statement to jump to an address specified by
a 'void*' variable, to make this work, you also need to take the address of a
label by using the unary operator '&&'
## &&
obtain the address of a label
the result is a 'void*' pointer which can be used with goto

# 内联函数
C99
GNU C
函数会在它所调用的位置上展开
定义一个内联函数时，需要使用 static 作为关键字，并且用 inline 限定它。
```c
static inline void wolf(unsigned long tail_size);
```
内联函数必须在使用之前定义好

# 内联汇编
```c
unsigned int low, high;
asm volatile("rdtsc" : "=a" (low), "=d" (high);
```
