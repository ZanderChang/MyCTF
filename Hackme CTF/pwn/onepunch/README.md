    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x400000)

程序可以向指定地址写入单个字节，而程序段可写，则修改jz跳转偏移即可形成循环结构，从而连续输入shellcode

    0x00400000  0x00401000  rwxp    /home/zander/Desktop/ctf/onepunch