# Object file (Executable file)
Its information are storage with `Section`(`Segment`) form.
- `Code Section`: `.code` or `.text`
- `Data Section`: `.data`
## `.text`
保存执行语句编译成的机器代码。
## `.data`
保存已初始化的**全局变量**和**局部变量**。
## `.bss`
为未初始化的全局变量和局部静态变量预留位置，它并没有内容，所以不占空间。
> 未初始化的全局变量和局部静态变量默认值都为 0。

# Section Table
描述文件中各个段的数组。

