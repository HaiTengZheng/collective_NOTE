# 配置选项
以 CONFIG_FEATURE 形式表示
前缀    CONFIG
e.g. CONFIG_SMP     多对称处理器的配置选项
## 配置项选择
- yes
- no
- module
module 意味着以模块 (一种可以动态安装的独立代码段) 的形式生效
## 配置工具
- make config       字符界面
- make menuconfig   基于 ncurse 库编制的图形界面 (recommend)
- make gconfig      基于 gtk+ 的图形工具
## 默认编译
基于默认的配置为你的体系结构创建一个配置
> make defconfig
## .config
存放配置项
## 验证和更新配置
> make oldconfig
## System.map
符号对照表

# 安装
## 模块的安装
> make modules_install
安装到 /lib/modules


