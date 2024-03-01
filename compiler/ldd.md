# ldd
可以显示出客户二进制文件启动时需要静态加载的动态库的完整列表(即加载时依赖项)
## 限制
- ldd 无法识别出运行时通过 dlopen() 函数动态加载的动态库

# 更安全的方法代替 ldd
> objdump -p /path/to/program | grep NEEDED
or 
> readelf -d /path/to/program | grep NEEDED
