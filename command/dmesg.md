# dmesg
把系统中与硬件相关的日志列出来, 保持在内存中

> print or control `kernel-ring buffer`

在进行系统引导时, 内核会将硬件和模块初始化相关的信息写到内核环形缓冲区

内核缓冲区的内容同时会保留在 `/var/log` 中

## remark: /var/log/dmesg
该文件是日志文件, 与 dmesg 无关

## see human-readable temestamps
> dmesg -T

## certain logging levels
such as errors and warnings
> dmesg -l err,warn
