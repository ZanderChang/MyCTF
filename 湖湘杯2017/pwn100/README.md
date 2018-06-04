    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x8048000)

#### fork()
子进程复制父进程的数据段（包括data和bss）、栈和堆，父、子进程共享正文段。对于程序中的数据，子进程要复制一份，但是对于指令，子进程并不复制而是和父进程共享。

#### wait(0)：等待任意一个子进程退出