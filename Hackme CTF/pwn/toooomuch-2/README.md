[参考](https://blog.csdn.net/niexinming/article/details/78796408)

由于libc开启PIE，无法使用jmp esp的方法。

通过strcpy溢出调用gets函数，把/bin/sh写入bss段，然后再利用pop_ret把gets的参数弹出，然后再调用system函数，把bss段的中的/bin/sh

注意跳转到call和直接跳转到被调用函数的区别：后者需要手动填充返回地址后再写入参数