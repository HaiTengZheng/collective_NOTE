# 避免意外覆盖文件
> set -o noclobber
noclobber 选项告诉 bash 在重定向向输出时不要覆盖任何现有文件
仅针对 shell 重定向输出时文件覆盖的行为，不能阻止其他程序覆盖文件

## >|
使用 `>|` 重定向输出，即使设置了 noclobber，bash 也会忽略该选项，并覆盖文件

# !!
(bang bang)
重复上一个命令
## !!:
类似于 sed 的替换
> !!:s/H/A/
### !!:g
g 表示全局替换
> !!:gs/s/S/

# 快速替换
^
> ^-g -A^-gB^
```
/usr/bin/somewhere/someprog -g -A -yknot -w /tmp/soforthandsoon

/usr/bin/somewhere/someprog -gq -yknot -w /tmp/soforthandsoon
```

# 参数重用
!:1     第一个参数
!:2     第二个参数
