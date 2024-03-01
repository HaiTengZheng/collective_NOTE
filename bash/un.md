# `.` and `source`
功能相同, 先加载脚本或配置文件, 处理完后加载到脚本下, 可保留变量或函数

# `sh` and `bash`
执行脚本都会启动新的 child shell 执行, 执行完后退回 parent shell
    无法保留变量或函数值

# 符号 ``
打印命令用反引号 `
e.g.
> userdir=`pwd`

# 
- 变量内容一般加双引号

# 查看设置变量
- set           (输出所有的变量)
- env           (只显示全局变量)
- declare       (输出所有的变量, 函数, 整数和已经导出的变量)

# gzip
files compressed by gzip can be directly concatenated into larger gzipped files
> cat file1.gz file2.gz file3.gz > combined.gz

# reomve an alias
> unalias {alias_name}

#  
```bash
cd "$(dirname "$(readlink -f "$0")")"
# readlink -f "$0" determines the path to the current script ($0)
```

# hexdump
> od -cH
or use `xxd`
> printf "content" | xxd
