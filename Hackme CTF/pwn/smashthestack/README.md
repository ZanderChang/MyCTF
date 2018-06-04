    Canary found
    NX enabled

#### SSP(Stack Smashing Protector) leak
[参考](http://j00ru.vexillium.org/blog/24_03_15/dragons_ctf.pdf)可知，canary校验失败后调用__stack_chk_fail显示__libc_argv[0]的内容，即将该处溢出为flag在内存中的地址即可