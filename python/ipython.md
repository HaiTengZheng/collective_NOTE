# ?
用于浏览文档

# ??
用于浏览源代码

# help()
获取 docstring

# magic commands
## line magic
prefix: %
- %paste        同时输入并执行代码
- %cpaste       打开一个交互式多行输入提示
- %run          执行外部代码
- %timeit?      ?, 获得帮助
- %magic        获得可用魔法函数的通用描述以及一些示例
- %lsmagic      列出可用魔法函数
- %history
- %cd
- %automagic
- %xmode
- %debug
- %pdb
- %time
- %timeit       计算代码运行时间
- %prun
- %lprun
- %memit
- %mprun
## cell magic
prefix: %%
- %%timeit
- %%time
- %%file

# In
> print(In)
一个列表，安装顺序记录所有的命令(列表中的第一个是一个占位符，以便 In[1] 可以表示
第一条命令)
# Out
> print(Out)
一个字典，将输入数字映射到相应的输出

# _
用于更新以前的输出
# __
倒数第二个
# ___
倒数第三个

# Out[X]
简写形式 _X

# ;
用于末尾，禁止一个命令的输出

# !
任何在 ! 之后的内容将不会通过 Python 内核运行，而是通过系统命令行运行。

# ext
> %load_ext line_profiler
> %load_ext memory_profiler
