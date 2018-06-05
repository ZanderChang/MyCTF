    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    No canary found
    NX:       NX enabled
    PIE:      No PIE (0x8048000)

#### 程序刚刚启动的时候，0是标准输入，1是标准输出，2是标准错误。[如果此时去打开一个新的文件，它的文件描述符会是3](https://blog.csdn.net/cywosp/article/details/38965239)

#### open后需要使用pop;ret;清空栈后再跳转。read后直接覆盖ret地址即可跳转。而且顺序不能交换。。这种通过直接跳转到main函数开头来反复调用main函数的方法存在一定问题。