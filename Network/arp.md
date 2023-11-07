# arp   
(ARP, Address Resolution Protocol)
用于操作和显示 arp 缓存区
> arp <option>
## 静态绑定 ip 地址与 MAC 地址
> arp -s 10.0.0.100 00:0c:29:c0:5a:ef
## 删除静态 arp 绑定
> arp -d 10.0.0.100
