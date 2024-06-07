--------------------------------------------------------------------------------
# list all built-ins with a short description
> help -d

--------------------------------------------------------------------------------
# enable
enable and disable builtin shell command.
## 关闭 shell builtin command
> enable -n builtin_name

--------------------------------------------------------------------------------
# read
reads one line of data from standard input into the variable
```bash
read line
echo "$line"
```
如果用户输入的单词数较少，多出的变量就会被设为 null。如果用户输入的单词数多于变
量数，则多出的单词会全部赋给最后的那个变量
## -p
在读取用户输入先输出提示信息
## -t
设置超时值

--------------------------------------------------------------------------------



