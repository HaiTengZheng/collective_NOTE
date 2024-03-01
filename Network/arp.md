# arp   
(ARP, Address Resolution Protocol)
用于操作和显示 arp 缓存区
> arp <option>
## 静态绑定 ip 地址与 MAC 地址
> arp -s 10.0.0.100 00:0c:29:c0:5a:ef
## 删除静态 arp 绑定
> arp -d 10.0.0.100

# MAC addresses
- the addresses that are burnned into each network interface
12-digit(6-byte/48-bit) address, normally shown in hexadecimal. When displayed,
each byte or double-byte is ususlly separated by . or -.
> 00-0c-29-3b-73-cb
or
> 9a93.5d84.5a69
