    amd64-64-little
    NX enabled
    PIE enabled

#### setvbuf() - 设定文件流缓冲区
    int setvbuf(FILE * stream, char * buf, int type, unsigned size);
    stream - 文件流指针
    buf - 缓冲区首地址
    type - 缓冲区类型
    size - 缓冲区内字节的数量
    成功返回0，失败返回非0

type | 说明
---- | ----
_IOFBF (满缓冲) 0 | 对于输出，数据在缓冲填满时被一次性写入。对于输入，缓冲会在请求输入且缓冲为空时被填充
_IOLBF (行缓冲) 1 | 对于输出，数据在遇到换行符或者在缓冲填满时被写入，具体视情况而定。对于输入，缓冲会在请求输入且缓冲为空时被填充，直到遇到下一个换行符
_IONBF (无缓冲) 2 | 不使用缓冲。每个 I/O 操作都被即时写入。buffer 和 size 参数被忽略

#### vmmap 
Get virtual mapping address ranges of section(s) in debugged process

#### [从指定目录加载动态链接库](http://blog.plusls.cn/technical/binary/pwn/load-so/)
    export LD_LIBRARY_PATH=/home/zander/Desktop/ctf:$LD_LIBRARY_PATH

#### [使用hn写入](https://blog.csdn.net/niexinming/article/details/78512274)为何要-19？而[hhn写入](https://blog.csdn.net/charlie_heng/article/details/78940020)就没有问题

#### 利用printf格式字符串漏洞动态获取基地址并修改exit的GOT表，使其指向libc中的[magic](https://github.com/LFlare/picoctf_2017_writeup/blob/master/binary/config-console/solve.py)处
    .text:00000000000F0897                 mov     rax, cs:environ_ptr_0
    .text:00000000000F089E                 lea     rsi, [rsp+1D8h+var_168]
    .text:00000000000F08A3                 lea     rdi, aBinSh     ; "/bin/sh"
    .text:00000000000F08AA                 mov     rdx, [rax]
    .text:00000000000F08AD                 call    execve