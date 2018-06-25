    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x8048000)

## IDA技巧-转换自定义结构数组
### 在`Structures`视图中创建自定义数组定义；
    00000000 st              struc ; (sizeof=0x8, mappedto_5)
    00000000 func            dd ?
    00000004 msg_ptr         dd ?                    ; XREF: deleteNote+88/r
    00000008 st              ends
### 对`ptr`变量按`y`键修改变量声明为`st *ptr[5]`。

## [pwndbg](https://github.com/pwndbg/pwndbg)
pwndbg提供heap命令查看堆块的分配情况，bins命令快速查看bins的状态
