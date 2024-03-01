# 库
> 一组预先编译好的函数的集合，库文件的名字总是以 lib 开头。
------------------------------------------------------------------------
remark: 文中 object 仅用来代替具体名称
------------------------------------------------------------------------
# 动态库
动态链接到使用它的二进制文件，库的代码不包含在二进制中
## 标准文件名
> lib + <library name> + .so + <library version information>
## 版本信息
> <M>.<m>.<p>
- M: 主版本号
- m: 次版本号
- p: 补丁版本号
## soname
> lib + <library name> + .so + <library major version digits>
## 优点
- 二进制文件尺寸更小
- 库可以被更新，而不需要重新编译二进制程序
## 缺点
不能从系统中移动或删除库
# 编译
> gcc -Wall -Wextra -pedantic -std=cc99 object.c -o object -lobject
------------------------------------------------------------------------
# 创建动态库
## 创建目标文件
使用 -fPIC 选项告诉 GCC 生成位置无关代码(PIC)，允许代码在不同进程的不同
地址处执行
```
gcc -Wall -Wextra -pedantic -std=c99 -c -fPIC object.c
```
## 创建动态目标文件
- -shared 表示创建一个共享对象
- -Wl 意味着将多有以逗号分隔的选项传递给链接器
- -soname,libobject.so 选项 -soname 将动态库名称设置为 libobject.so,
  soname 是共享对象名称的缩写，它是库中的内部名称，作为引用时使用
- -o 指定输出文件的名称(真实名称)
使用包含版本号的真实名称是标准约定 libobject.so.1.3 大版本 1，小版本 3
真实名称和 soname 都必须以 lib 开头
```
gcc -shared -Wl,-soname,libobject.so -o libobject.so.1 object.o
```
动态库可以在被清除符号信息的情况下工作，但必须在创建动态库之后的 .so 
文件上进行清除

.so 文件将符号保存在名为 .dynsym 的特殊表中，strip 命令不会触及该表
可以使用 readelf --symbols 选项在被清除符号的动态库上查看此表
# 安装动态库
将库文件与头文件移动到正确的目录
头文件：/usr/local/include/
库文件：/usr/local/lib/
```bash
sudo install -o root -g root -m 755 \
libobject.so.1 /usr/local/lib/libobject.so.1
```
```bash
sudo install -o root -g root -m 644 object.h \
/usr/local/include/object.h
```
fedora 中需要将 /usr/local/lib/ 放入 ldconfig 的默认搜素路径
```bash
echo "/usr/local/lib" >> /etc/ld.so.conf.d/local.conf
```
## 创建必要的链接并更新缓存
> sudo ldconfig
------------------------------------------------------------------------







------------------------------------------------------------------------
# 静态函数库
也称归档文件(archive)，以 .a 结尾
包含在二进制中
> lib + <library name> + .a
## 优点
一旦编译，二进制文件将完全独立于库
## 缺点
当同时运行许多应用程序并且它们都使用来自同一个函数库的函数时，内存中
会有同一个函数的多份副本，而且在程序文件中也有多份同样的副本。这将消
耗大量的内存和磁盘空间。
# 编译(放在动态库同一位置)
> gcc -Wall -Wextra -pedantic -std=c99 -static object.c -lobject -o object
------------------------------------------------------------------------
# 创建静态库
## 编译成目标文件
> gcc -Wall -Wextra -pedantic -std=c99 -c object.c
## 查看目标文件
> file object.o
结果可见到 not stripped (符号信息未被清除)
## 打包到存档文件中
- -c 表示创建存档文件
- -v 表示详细输出信息
- -r 表示替换同名成员
> ar -cvr libobject.a object.o
## 查看静态库
> nm libobject.a
------------------------------------------------------------------------
# 从二进制文件中清除符号
> strip object
静态库不能被清除符号，否则链接器看不到函数，链接失败
------------------------------------------------------------------------
# 查看库的内部
> nm
------------------------------------------------------------------------ 


# 标准 C 语言函数库
- /usr/lib/libc.a 
# X11 函数库
- /usr/lib/libX11.a 
# ar
建立归档文件程序，它将若干单独的文件归并到一个大的文件中以创建归档文件或集合。
e.g.
> ar crv libfoo.a bill.o fred.o
# ranlib
UNIX 中需要为函数库生成一个内容表，通过 ranlib 命令。使用 GNU 软件开发工具时无需。
e.g.
> ranlib libfoo.a


# 共享函数库
.so

链接方式：程序本身不再包含函数代码，而是引用运行时可访问的共享代码。当编译好的程序被装载到内存中执行时，函数引用被解析并对共享库的调用，如果有必要，共享库才被加载到内存中。

# ld.so
负责装载共享库并解析客户端函数引用的程序（动态加载库）

# 查看一个程序需要的共享库（运行工具 ldd)
e.g.
> ldd program

