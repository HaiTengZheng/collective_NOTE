# awk/gawk
pattern scanning and processing language
> awk <options> <pattern(action)> file
- 一行就是一个记录
- 一个记录有若干个字段

# 常用功能 
 - 指定分隔符显示 
 - 通过正则表达式取出你想要的内容
 - 显示某个范围内的内容
 - 通过 awk 进行统计计算
 - awk 数组计算与去重

# {}
花括号用于将几块代码组合到一起

# print
在 awk 中, 如果只出现 print 命令, 那么将打印当前行的全部内容

# FS
字段分隔符
> awk -F":"

# NF
字段数量

# NR
记录数量

# BEGIN 模块
在开始处理输入文件中的文本之前执行初始化代码
> awk 'BEGIN{a=5;a+=5;print a}'

# END 模块
 在处理了输入文件中的所有行之后执行
- 通常用于执行最终计算或打印摘要
