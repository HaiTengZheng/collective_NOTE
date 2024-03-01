# socket
> <sys/socket.h>    socket 的主要 API
> <netdb.h>         网络信息 API，以实现主机名和 IP 地址之间的转换，以及服务名称
                    和端口号之间的转换
## 字节序
- 主机字节序        little-endian       
- 网络字节序        big-endian
### 字节序转换
> <netinet/in.h>
- htonl()           /* host to network long (32 bit) */
- htons()
- ntohl()
- ntohs()
long -> IP address
short -> socket

## 通用 socket 地址
> <bits/socket.h>
> <sys/socket.h>
<bits/socket.h> 不能直接使用，应使用 <sys/socket.h>
```c
/* old version */
#include <bits/socket.h>
struct socktaddr {
    sa_fmaily_t sa_fmaily;
    char sa_data[14];       /* 存放 socket 地址值 */
}
/* sa_data 无法容纳多数协议族的地址 */
/* new general edition */
struct socktaddr_storage {
    sa_fmaily_t sa_fmaily;
    unsigned long int __ss_align;
    char __ss_padding[128 - sizeof(__ss_align)];
}
/* __ss_align 用于内存对齐 */
```
## sa_fmaily
> <bits/socket.h>
- PF_* (protocol fmaily, domain)
- AF_* (address fmaily)
### PF 
- PF_UNIX       108 bytes
- PF_INET       16 bit 端口号，32 bit IPv4 地址
- PF_INET6      16 bit 端口号，32 bit 流标识，128 bit IPv6 地址，32 bit 范围 ID
### AF
- AF_UNIX
- AF_INET
- AF_INET6

## 专用 socket 地址
> <sys/un.h>
- unix      sockaddr_un
> <sys/in.h>
- IPv4      sockaddr_in, in_addr
- IPv6      sockaddr_in6, in6_addr
所有的专用 socket 地址(以及 socktaddr_storage) 都需要转化为通用 socket 地址类型
sockaddr(强制转化即可)，因为所有 socket 编程接口使用的地址参数类型都是 sockaddr

## IP 地址转化函数
> <arpa/inet.h>
- inet_addr()       讲点分十进制字符串表示的 IPv4 地址转化为网络字节序整数表示的
                    IPv4 地址，失败返回 INADDR_NONE
- inet_aton()       转化结果存储于参数 inp 指向的地址结构中，ok -> 1, error -> 0
- inet_ntoa()       将网络字节序整数表示的 IPv4 地址转化为点分十进制字符串表示的
                    IPv4 地址。需要注意的是，该函数内部用一个静态变量存储转化结
                    果，函数的返回值指向该静态内存，因此 inet_ntoa 不可重入
- inet_pton()       IPv4, IPv6, 存储进 dst， Ok -> 1, error -> 0
- inet_ntop()       Ok -> 目标存储地址，error -> NULL 并设置 errno

# create socket
```c
#include <sys/types.h>
#include <sys/socket.h>
int socket(int domain, int type, int protocol);
```
- domain:   协议族
- type:     服务类型
- protocol: 在前两个参数构成的协议集合下，在选择一个具体的协议，0 -> 默认协议

# bind
```c
int bind(int sockfd, const struct sockaddr* my_addr, socklen_t addrlen);
/* success -> 0, fail -> -1 and set errno */
/*  errno: EACCES       被绑定的地址是受保护的地址
 *         EADDRINUSE   被绑定的地址使用中
 */
```

# listen
```c
int listen(int sockfd, int backlog);
/* backlog: 内核监听队列的最大长度，超过 -> ECONNREFUSED
 * 2.2 之后表示处于完全链接状态的 socket 的上限，处于半链接的上限则
 * 由 /proc/sys/net/ipv4/tcp_max_syn_backlog 内核参数定义
 */
 /* success -> 0, fail -> -1 and set errno */
```

# accept
```c
int accept(int sockfd, struct sockaddr *addr, socklen_t *addrlen);
```
accept 只是从监听队列中取出连接，而不论链接处于何种状态，更不关心任何网络状态的
变化

# connect
```c
int connect(int sockfd, const struct sockaddr *serv_addr, socklen_t addrlen);
/* success -> 0, fail -> -1 and set errno */
/* errno : -ECONNREFUSED 
 *         -ETIMEOUT
 */
```

# close
```c
int close(int fd);
int shutdown(int sockfd, int howto);
```
close 系统调用并非总是立即关闭一个连接，而是将 fd 的引用计数减 1，只有当 fd 的引
用计数为 0 时，才真正的关闭连接
无论如何都要立刻终止连接 ----- 使用 shutdown 系统调用

# 数据读写
## tcp
```c
#include <sys/types.h>
#include <sys/socket.h>
ssize_t recv(int sockfd, void *buf, size_t len, int flags);
ssize_t send(int sockfd, const void *buf, size_t len, int flags);
```

## udp
```c
ssize_t recvfrom(int sockfd, void *buf, size_t len, int flags,
                 struct sockaddr *src_addr, socklen_t *addrlen);
ssize_t send(int sockfd, const void *buf, size_t len, int flags,
             const struct sockaddr *dest_addr, socklen_t addrlen);
```
