# objdump
用于反汇编二进制文件
- AT&T is default
> objdump -D code.o
- use intel format
> objdump -D -M intel code.o
## 对含有未初始化的 .bss 段进行反汇编操作
> objdump -x -j .bss app_name

## 解析 ELF 头
> objdump -f <target-file>
## 列出并查看节信息
> objdump -h 
## 列出所有符号
> objdump -t <path-to-binary>
equal to
> nm <path-to-binary>
## 只列出动态符号
> objdump -T <path-to-binary>
equal to
> nm -D <path-to-binary>
