# ifconfig  (命令已过时)
ifconfig 在配置网卡信息时必须以 root 用户的身份来执行
> ifconfig <interface> <option>
## 查看网卡
> ifconfig
> ifconfig -a
## 开启网卡
> ifconfig eth0 up
## 关闭网卡
> ifconfig eth0 down
## 为网卡配置地址
> ifconfig eth0 192.168.3.3
## 为网卡配置子网掩码
> ifconfig eth0 netmask 255.255.255.0
## 为网卡配置别名
> ifconfig eth0:0
## 修改网卡的 MAC 地址
> ifconfig eth0 hw ether 00:AA:BB:CC:DD:EE

# 物理配置路径
> /etc/sysconfig/network-scripts/ifcfg-eth0
(已不使用)
