初步使用ROPgadget

    ROPgadget --binary rop --ropchain

ROPgadget在使用`--ropchain`自动生成payload时需指定python2，直接修改`$(which ROPgadget)`的头部即可，参见：https://www.cs.virginia.edu/~cr4bd/4630/S2017/assignments/rop.html