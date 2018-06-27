    Arch:     i386-32-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x8048000)

## [Top Chunk](https://www.cnblogs.com/alisecurity/p/5486458.html)
### 概念
当一个chunk处于一个arena的最顶部（即最高内存地址处）的时候，就称之为top chunk。该chunk并不属于任何bin，而是在系统当前的所有free chunk（无论哪种bin）都无法满足用户请求的内存大小的时候，将此chunk当做一个应急消防员，分配给用户使用。

如果top chunk的大小比用户请求的大小要大的话，就将该top chunk分作两部分：

1）用户请求的chunk；

2）剩余的部分成为新的top chunk。

否则，就需要扩展heap或分配新的heap：在main arena中通过sbrk扩展heap，而在thread arena中通过mmap分配新的heap。

### 利用
交换两块可写地址的值：Top chunk和got@read

## 参考
https://blog.csdn.net/niexinming/article/details/78759363

http://www.freebuf.com/articles/rookie/155971.html
