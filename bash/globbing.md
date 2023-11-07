# 模式
任何包含字符 * ? [ 的字符串会被依字符排序的、匹配该模式的文件名列表所替代
- *	匹配包括空串在内的任意字符串
- ?	匹配任意单个字符
- [] 匹配其中的任意个字符
- [!] or [^] 匹配不在其中的任意单个字符
> remark: ! 是 POSIX 规定的，移植性更好
## POSIX 字符类
> grep --help
> egrep --help
- [:alnum:]
- [:alpha:]
- [:ascii:]
- [:blank:]
- [:cntrl:]
- [:digit:]
- [:graph:]	非控制、非空格字符
- [:lower:]
- [:print:]
- [:punct:] 标点符号字符
- [:space:] 空白字符，包括垂直制表符
- [:upper:]
- [:xdigit:]
