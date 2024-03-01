# nm
列出二进制文件的符号列表
## 列出二进制文件的所有符号
> nm /path/to/binarynm
## 只列出动态节中的符号(即共享库中导出的或对外可见的符号)
(in the dynamic section)
> nm -D /path/to/binary
## 列出未经过名称修饰的格式
(in degmangle format)
> nm -C /path/to/binary
## 打印出共享库中名称修饰后的动态符号
> nm -D --no-demangle /path/to/binary
## 列出库中为定义的符号
(这个库文件本身并不包含该符号，但期望在运行时加载的其他动态库中提供)
> nm -u /path/to/binary
## -A
> nm -A <library-folder-path>/* | grep symbol-name
useful when you search for a symbol in multitude of binaries located in the same
folder, as `-A` option prints the name of each library in which a symbols is
found
