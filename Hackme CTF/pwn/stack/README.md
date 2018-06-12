    Arch:     i386-32-little
    RELRO:    Full RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      PIE enabled

#### [gdb调试多进程](https://blog.csdn.net/pbymw8iwm/article/details/7876797)
follow-fork-mode | detach-on-fork | 说明
--- | --- | ---
parent | on | 只调试主进程
child | on | 只调试子进程（默认）
parent | off | 同时调试两个进程，gdb跟主进程，子进程block在fork位置
child | off | 同时调试两个进程，gdb跟子进程，主进程block在fork位置

#### 思路
1、通过stack_pop栈来泄露程序基地址、libc基地址和栈地址；

2、通过stack_push写数据，覆盖stack_push的返回地址，跳到libc中执行exec("/bin/sh")的地址（MAGIC）

#### 关闭系统地址随机化
    sudo sh -c "echo 0 > /proc/sys/kernel/randomize_va_space"

#### PIC（位置无关代码） -fpic
https://github.com/DennisYurichev/reverse-engineering-for-beginners/blob/master/Chapter-67/Linux.md

1866h常量是这个函数开始处到（Global Offset Table Procedure Linkage Table(GOT PLT)）之间的距离差

#### __readgsdword
从偏移量的指定位置读取内存相对GS段开头

#### gdb-peda查看栈esp指针之上的栈空间内容
    peda telescope $sp-0x10

#### 程序运行过程可以Crtl+c后设置断点，查看vmmap等

#### 参考
https://blog.csdn.net/niexinming/article/details/78666941
