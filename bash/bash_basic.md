# bash

# $-
print the current set of optons in your current shell
> himBH
- h-histexpand      when history expansion is enabled
- m-monitor         when job control is enabled
- h-hashall         Locate and remember (hash) commands 
                    as they are looked up for execution
- b-braceexpand     when brace expansion is enabled
- i-interactive     when current shell is interactive

# \command_name
在命令名前使用反斜线可以避开所有的别名

# ''
strong quoting
无需扩展
无法在一对单引号中再嵌入另一个单引号，使用反斜线页不行，因为单引号内不会执行任何
    插值操作
解法: 1. 使用双引号以及转义字符 2. 在单引号对之外转义单引号

# ""
WEAK QUOTING
use escape to prevent expansion
```bash
world="World"
echo "Hello \$world"
```

# set
> set -- "I am" handsome oldboy
`--` 表示清楚所有的参数变量，重新设置后面的参数变量

# eval

# exec
能在不创建新的子进程的前提下，转去执行指定的命令，当指定的命令执行完毕后，该
    进程就终止了。
> exec date
当使用 exec 打开文件后，read 命令每次都会将文件指针移动到文件的下一进行读取，直
    到文件末尾，利用这个可以实现处理文件的内容。
```bash
exec < /tmp/tmp.log
while read line
do
    echo $line
done
echo ok
```

# $RANDOM
get a random number

# shebang
第一行的 #! 符号
它告诉系统同一行上紧跟在它后面的那个参数是用来执行本文件的程序。
(使用的是绝对路径，不要超过 32 位）
```bash
#!/bin/bash
```
```bash
#!/usr/bin/env bash
# the shebang tell the opreating system to search the computer's $PATH to find
#   the `bash` interpreter
```

# 注释
以 # 开头的行
```bash
#!/bin/bash
# comment sentences
```

# 命令替换
两种方法
- 反引号字符 ``
- $() 格式          (recommend)
```bash
show_date=`date`
show_date=$(date)
# remark: 赋值等号与命令替换符号之间没有空格
```
命令替换会创建一个 subshell 来运行对应的命令

# 重定向
## >
输出重定向
## <
输入重定向
## >>
追加数据
## <<
(inline input redirection) 内联输入重定向
- 必须指定一个文本标记来划分输入数据的开始与结尾。任何字符串都可以作为文本标记，
    但在数据的开始和结尾的文本标记必须一致
```bash
command << markder
    commands
markder
```
## >& or &> or 2>&1
将标准错误消息重定向到和标准输出相同的地方
## 1>&2
将标准输出的指向重定向到与标准错误相同的地方
## &>>
两者重定向追加
## 2&>3-
'-' 是为了操作完成后关闭文件描述符 3
## 交换 STDERR 和 STDOUT
> 3>&1 1>&2 2>&3
## 一行中多次重定向
> divert 3> file.three 4> file.four 5> file.five
## |$
> somecmd |$ othercmd

# 数学计算
数学表达式放入 $[]  中
```bash
var1=$[1 + 5]
```
- 只支持整数计算
## 浮点计算
使用 bc 命令

# 退出状态码
- 0 表示成功
- 1~125 脚本可以使用的错误代码
- 126 文件不可执行
- 127 命令未找到
- 128及以上 出现一个信号

# 条件测试
## test 或 [ ]
```bash
if test -f fred.c
then
commands
fi
```
remark: 必须在 [ ] 和被检查条件之间留出空格。
then 与 if 放在同一行上，必须用一个分号把 test 语句和 then 分离
```bash
if [ -f fred.c ]; then # then 放在同一行需要添加 ;
commands
fi
```
> man test

## 符合条件测试
### AND
> [ condition_1 ] && [ condition_2 ]
### OR
> [ condition_1 ] || [ condition_2 ]

## (( ))
高级数学表达式
```bash
if (( $val ** 2 > 90))
then
    commands
fi
```

## [[ ]]
提供了针对字符串比较的高级特性
- 模式匹配 (pattern matching)
```bash
if [[ $USER = r* ]]
```

# IFS
内部字段分离符号 (internal field separator)
```bash
# 保证 IFS 修改后恢复 e.g.
IFS.OLD=$IFS
IFS=$' \t\n'
IFS=IFS.OLD
```

# Range
```bash
for i in {1..5}; do # {1..5} means 1 2 3 4 5
    commands
done
```

# 参数扩展 (important)
## ${#name}
给出 name 的长度
## ${name%pattern}
从 name 的尾部开始删除与 pattern 匹配的最小部分，然后返回剩余部分
## ${name%%pattern}
从 name 的尾部开始删除与 pattern 匹配的最长部分，然后返回剩余部分
## ${name#pattern}
从 name 的头部开始删除与 pattern 匹配的最小部分，然后返回剩余部分
## ${name##pattern}
从 name 的头部开始删除与 pattern 匹配的最小部分，然后返回剩余部分
## ${name:number:number}
从字符串 name 的索引位置 number 开始，返回长度为 number 的子串
## ${name/pattern/string}
替换字符串中第一次出现的 pattern
## ${name//pattern/string}
替换字符串中出现的所有 pattern

# 特殊扩展变量
> man bash
search "Parameter Expansion"

- : 可选
## ${parameter:-word}
如果 parameter 的变量值为空或未赋值，则会返回 word 字符串并替代变量的值
用途 : 如果变量未定义，则返回备用的值，防止变量为空值或因为定义而导致异常
## ${prameter:=word}
如果 parameter 的变量值为空或未赋值，则设置这个变量值为 word，并返回其值
用途 : 基本同上一个 ${parameter:-word}，但该变量又额外给 parameter 变量赋值
## ${parameter:?word}
如果 parameter 的变量值为空或未赋值，那么 word 字符串将被作为标准错误输出，否则
    则输出变量
用途 : 用于捕捉由于变量未定义而导致的错误，并退出程序
## ${parameter:+word}
如果 parameter 变量值为空或未赋值，则什么都不做，否则 word 字符串将替代变量值


