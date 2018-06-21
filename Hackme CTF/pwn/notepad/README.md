    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x8048000)

#### 思路
1、notepad_open中menu未检验输入下限，导致返回负数；

2、notepad_open通过menu的返回值调用note结构体中保存的notepad_show函数地址；

3、0号文件写入printf和strncpy地址 -> 新建1号文件 -> 修改1号文件为printf参数 -> menu返回负数call strncpy，覆盖note[1].notepad_show -> 打开1号文件 -> menu返回负数call printf，暴露lib基地址 -> 修改0号文件为MAGIC，通过修改1号文件调用