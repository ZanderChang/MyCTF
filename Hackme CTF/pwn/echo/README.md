    NX enabled

#### 格式化字符串漏洞

    %p - 指针，64位和32位不同

    %n - 到目前为止所写的字符数
    printf("ABCDE%n", &i); // i = 5

    n$ - 选取第n个参数
    printf("ABCDE%3$n", &a, &b, &c); // c = 5

格式 | 目标空间大小(Byte)
---- |:---:
$hh | 1
$h |  2
$ | 4
$ll | 8

    %p - 输出16进制数据，与%x基本一样，只是附加了前缀0x，在32bit下输出4字节，在64bit下输出8字节，可通过输出字节的长度来判断目标环境是32bit还是64bit。

[pwntools中的FmtStr方法寻找偏移](http://pwntools.readthedocs.io/en/stable/fmtstr.html#module-pwnlib.fmtstr)

参考：https://paper.seebug.org/246/

利用fmtstr_payload修改printf函数的got表指向system，下一次循环输入/bin/sh即可返回shell

PLT表不能被修改，只能修改GOT

    plt[1] = jmp got[1]

    got[1] = got2 -> jmp got2 错误

    got[1] = plt2 -> jmp plt2 -> jmp got[2] 正确