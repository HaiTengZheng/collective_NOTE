# thread-local
thread-local storage (TLS)
存储数据到全局变量中，每个线程都有这个存储变量的副本，线程不会分享这个数据，副本
是线程独有的，所以对它的访问不需要同步控制。
## thread_local!
创建 thread-local key, 它可以包含 'static 的值，使用 with 访问函数去访问值


# thread-priority
设置线程的优先级


# affinity 
将线程绑定在一个核上或者几个核上

# unwind

# crossbeam
scpoed thread on scpoed thread

# rayon

# send_wrapper
