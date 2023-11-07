```bash
#!/usr/bin/env bash
# the first line with #! is `shebang`
# cookbook filename: security_template

# set a sane/secure path
PATH='/usr/local/bin:/bin:/usr/bin'
# It's almost certainly already marked for export, but make sure
\export PATH

# clear all alias, Important: leading \ inhibits alias expansion
\unalias -a

# clear the command path hash
hash -r

# set the hard limit to 0 to turn off core dumps
ulimit -H -c 0 --

# set s sane/secure IFS (note this is bash & ksh93 syntax only-not portable
IFS=$' \t\n'

# set a sane/secure umask variable and use it
# note this does not affect files already redirected on the command line
# 022 results in 0755 perms, 077 results in 0700 perms, etc.
UMASK=022
umask $UMASK

until [ -n "$temp_dir" -a ! -d "$temp_dir" ]; do
    temp_dir="/tmp/meaningful_prefix.${RANDOM}${RANDOM}${RANDOM}
done
mkdir -p -m 0700 $temp_dir \
    || (echo "FATAL: Failed to create temp dir '$temp_dir': $?"; exit 100)

# do our best to clean up temp files no matter what
# note $temp_dir must be set before this, and must not change
cleanup="rm -rf $temp_dir"
trap "$cleanup" ABRT EXIT HUP INT QUIT
```

```bash
#!/usr/bin/env bash

# 设置合理的/安全的路径
PATH='/usr/local/bin:/bin:/usr/bin:'
# 确保导出 $PATH
\export PATH

# 清除所有的别名。切记： 开头的\用于禁止别名扩展
\unalias -a

# 清除命令路径散列
hash -r

# 将硬性限制设置为 0，关闭核心转储 (core dumps)
ulimit -H -c 0 --

# 设置合理的/安全的 IFS（此处语法仅适用于 bash 和 ksh93，不具备可移植性）
IFS=$' \t\n'

# 设置并使用合理的/安全的 umask 变量
# 注意；这不会影响已经在命令行上的命令
# 022 产生 0755 权限，077 产生 0700 权限...
UMASK=022
umask $UMASK

until [ -n "$temp_dir" -a ! -d "$temp_dir" ]; do
	temp_dir="/tmp/meaningful_prifix.${RANDOM}${RANDOM}${RANDOM}"
done
mkdir -p -m 0700 $temp_dir \
	|| (echo "FATAL: Failed to create temp dir '$temp_dir': $?"; exit 100)

# 尽全力清除临时文件
# 注意：一定要先设置好 $temp_dir 
cleanup="rm -rf $temp_dir"
trap "$cleanup" ABRT EXIT HUP INT QUIT
```
