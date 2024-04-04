# Make
- structured top-down
- bottom-up execute
- support whildcards which identical to the Bourne shell's
-------------------------------------------------------------------------------
# default rule
```Makefile
target_1 target_2: prereq_1 prereq_2
    command_1 \
    command_2
# comment
```
- one or more targets appear to the left of the colon
- zero or more prerequisites can appear to the right of the colon
- each commands must begin with a `tab` character, this (obscure) syntax
    tells make that the characters that follow the tab are to be passed to a
    `subshell` for execution
- long lines can be continued using the standard Unix escape character 
    backslash `\`, (commands, prerequisites is the same)

# target
> the file or thing that must be made
## phony target 假想工作目标
> targets that do not represent files
- make cannot distinguish between a file target and phony target, Gnu make
    includes a special target `.PHONY` to tell make that a target is not a
    real file
e.g. target is not a real 
```
.PHONY: target
target:
    command
```
- 将假想工作目标内置在 makefile 里的 shell 脚本使用
- 假想工作目标总是尚未更新, 所以它们总是被执行, 并且总是会使得它们的 targets 被
    重建
### all:
> 执行编译应用程序的所有工作
### clean:
> 将产生自源代码的二进制文件删除
### install 
> 从已编译的二进制文件进行应用程序的安装
### distclean
> 删除编译过程中所产生的任何文件(除了二进制文件, 也包含了 configure 所产生
    的 Makefile)
### info
> 从 Texinfo 源代码创建 Gnu info 文件
### check
> 执行与应用程序相关的任何测试
## nonphony target
only `TAGS`
### TAGS
> 建立可供编辑器使用的标记表

## empty target (cookie)
- 偶尔被执行


# prerequisites or dependents
> those files that must exit before the target be successfully created

# commands
> those shell commands that will create the target from the prerequisites

# comment
> the hash or pound sign `#`, all text from the pound sign to the end of line
    is ignored

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# variable
> 使用 $() 或 ${} 括住, 变量名称若是单一字符则不需要为它加上圆括号
## 自动变量
- $@    工作目标的文件名
- $%    档案文件成员 (archive member) 结构中的文件名元素
- $<    第一个必要条件的文件名
- $?    时间戳在工作目标(的时间戳)之后的所有必要条件, 并以空格隔开这些必要条件
- $^    所有必要条件的文件名, 并以空格隔开这些文件名. 这份列表已删除重复的文件
            名, 因为对大多数的应用而言, 比如编译, 复制等, 并不会用到重复的文件
            名
- $+    如同 $^, 代表所有必要条件的文件名, 并以空格隔开这些文件名. 不过, $+ 包
            含重复的文件名. 此变量会在特殊的状态下被创建, 比如将自变量传递给
            链接器 (linker) 时重复的值是有意义的
- $*    工作目标的主文件名. 一个文件名称由两个部分组成: stem 和 suffix    
            不要在模式规则以外使用此变量
e.g.
for archive file foo.a(bar.o), $@ is foo.a, $% is bar.o
## 兼容
### 变体 1
> 只会返回值的目录部分
在原有的符号之后附加 D 字母
> $(@D)
### 变体 2
> 只会返回值的文件部分
在原有的字符之后附加 F 字母
> $(@F)

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# 以 VPATH 的 vpath 查找文件 
e.g
```
VPATH = src include
```
## vpath
e.g.
```
vpath %.l %.c src
vpath %.h include
```

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# %
代表任意多个字符
可以放在模式中的任何地方, 不过只能出现一次

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# 内置规则
> make -p
> make --print-data-base

-------------------------------------------------------------------------------
-------------------------------------------------------------------------------
# 双冒号规则
一个模糊的功能, 依据必要条件的时间戳是否在工作目标的时间戳之后, 以不同的命令来
    更新同一个工作目标

