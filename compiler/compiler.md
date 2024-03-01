# 预处理
- -E 预编译后停止
- -P 使预处理器不在预处理文件中包含行标记
> gcc -E code.c -o code.i
> gcc -E -P code.c -o code.i
- -UTEST 向 gcc 传递未定义 TEST
- -DTEST 定义 TEST 宏

# 编译
将文件翻译为汇编语言
> gcc -S code.i -o code.s
- -S 在编译过程完成后停止
LFBx 和 LFEx 是局部符号，表示函数开始和结束，其中 x 数字用于区分各个函数
keyword: cfi -> Call Frame Infromation
## 汇编指导符
- .file         文件名
- .section      节名
- .string       字符串
- .global       全局符号
- .text         代码节
## -masm=
- AT&T
> gcc -S -masm=att code.c -o code.s
- Intel
> gcc -S -masm=intel code.c -o code.s

# 汇编
将汇编代码文件构建为所谓的目标文件
> gcc -c code.s -o code.o
- -c 在汇编之后停止
## objdump -d 
查看经反汇编得到的代码

# 链接
> gcc code2.c code2.c -o code


# ELF
> https://man7.org/linux/man-pages/man5/elf.5.html
> man elf
