# rules
此处用 `` 来标注，而非 bash 中的命令执行符号
```bash
#!/usr/bin/env bash
## 第一行指定脚本解释器

# Date      : 17:00 2023-11-23
# Author    : haiteng.zheng
# Mail      : haiteng.zheng@outlook.com
# Function  : The scripts function is
# Version   : 1.1
## 加上版本等信息

## 使用英文注释
## shell 脚本以 `.sh` 命名
## 字符串赋值给变量时应加双引号，并且等号前后不能有空格
TARGET_FILE="test.file"
## 全局变量应该全部大写，多个单词以 `_` 连接
## 局部变量可使用 `local` 定义
function TestFunc() {
    local i
}
## 若引用变量前后都有字符，则使用 `${}` 的方法引用
### ${APACHE_ERR}
## 若变量内容为字符串时，需要使用 `"${}"` 的方法引用
### "${APACHE_ERR}"
## 若变量为整数
### $APACHE_ERR

## 命名规范
## 常用 shell 脚本
### name.sh
## 启动
### start_name.sh
## 暂停 
### stop_name.sh
## 监控
### name_mon.sh
## 控制
### name_ctl.sh

## 代码规范树
## |-- bin
## |   `-- ipsecctl
## |-- conf
## |   `-- ipsec.cfg
## `-- func
##     `-- functions
## 通用变量以配置文件的形式单独存放，以 `功能.cfg` 命名，并放入 conf 目录

## http 脚本变量的定义方式
http=${HTTPD-/usr/sbin/httpd}
prog=httpd
pidfile=${PIDFILE-/var/run/httpd.pid}
lockfile=${LOCKFILE-/var/lock/subsys/httpd}
```
