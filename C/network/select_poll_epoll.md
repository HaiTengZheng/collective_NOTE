# I/O 多路复用
支持应用同时在多个文件描述符上阻塞，并在其中某个可以读写时收到通知。
- select
- poll
- epoll

# select()
一种实现同步 I/O 多路复用的方法
level triggered
> man 2 select
```c
#include <sys/select.h>
#include <sys/time.h>
/* 基于文件描述符的三位掩码 */
int select(int nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds,
           struct timeval *timeout);
/* nfds = 所有集合中文件描述符的最大值 + 1 */
/* exceptfds 监视是否发生异常，或者出现 out-of-band 数据(这些场景只适用于
 * socket)
 * success -> 0, fail -> -1 and set errno 
 * errno: -EBADF
 *        -EINTR
 *        -EIVAL
 *        -ENOMEM
 */
struct timeval {
    long tv_sec;    /* secons，不可靠 */
    long tv_usec;   /* microseconds */
}

fd_set 
FD_ZERO /* 每次使用 select() 之前都应该调用该宏 */
FD_SET  /* 向指定集中添加一个文件描述符 */
FD_CLR  /* 从指定集中删除一个文件描述符 (极少使用) */
FD_ISSET /* 检查一个文件描述符是否在给定的集合汇中 */
/* fd < FD_SIZE (1024) */
```
在给定的文件描述符 I/O 就绪之前且还没有超出指定的时间限制 select() 调用就会
阻塞
## pselect()
POSIX 1003.1-2001
```c
#define _XOPEN_SOURCE 600
#include <sys/select.h>
int pselect(int n, fd_set *readfds, fd_set *writefds, fd_set *exceptfds,
            const struct timespec *timeout, const sigset_t *sigmask);
/* sigmask，是为了解决文件描述符和信号之间等待而出现的竞争条件 */
```

# poll()
是 System V 的 I/O 多路复用的解决方案
level triggered
```c
#include <poll.h>
/* 由 nfds 个 pollfd 结构体组成的数组 */
int poll(struct pollfd *fds, nfds_t nfds, int timeout);
struct pollfd {
    int     fd;         /* file descriptor */
    short   events;    /* requested events to watch */
    short   revents;    /* returned events witnessed */
}
/* 不需要显式请求异常报告 */
```
## ppoll()
Linux 特有的调用
```c
#define _GNU_SOURCE
#include <poll.h>
int ppoll(struct pollfd *fds, nfds_t nfds, const struct timespec *timeout,
          const sigset_t *sigmask);
```

# event poll (epoll)
epoll 把监听注册从实际监听中分离出来
一个系统调用会初始化 epoll 上下文，另一个从上下文中加入或删除监视的文件描述符，
第三个执行真正的事件等待 (event wait)
