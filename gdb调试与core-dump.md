# [gdb调试与coredump.md](gdb%B5%F7%CA%D4%D3%EBcoredump.md)



## linux coredump
1. 取消coredump文件大小限制：ulimit -c unlimited
2. 设置和查看coredrump文件存储位置：sudo sysctl -w kernel.core_pattern=/home/eswin/Desktop/core-%e-%s-%u-%g-%p-%t  && cat /proc/sys/kernel/core_pattern
3. 运行程序并等待崩溃。
4. gdb分享coredump：gdb buKaInteractionClient /home/eswin/Desktop/core-buKaInteraction-11-1000-1000-11247-1658827857

coredump信息
- %p：进程ID。
- %u：用户ID。
- %g：用户所属组ID。
- %s：导致dump的信号的数字。
- %t：dump的时间。
- %e：执行文件的名称。
- %h：主机名

## gdb操作
堆栈操作：
```
gdb xxx.exe
set args -c xxx.conf
r run
n next
c continue
stop
start
step
finish
```
```
bt full
up 1
down 1
i frame
```
线程操作
```
//1.查看进程：info inferiors
//2.查看线程：info threads
//3.查看线程栈结构：bt
//4.切换线程：thread n（n代表第几个线程）
```
查看信息：
```
b 变量名
info
```

### gdb运行配置文件: .gdbinit
```
define bbsave
     shell rm -f brestore.txt
     set logging file brestore.txt
     set logging on
     info break
     set logging off
     # reformat on-the-fly to a valid gdb command file
     shell perl -n -e 'print "break $1\n" if /^\d+.+?(\S+)$/g' brestore.txt > brestore.gdb
end
document bbsave
   store actual breakpoints
end
define bbrestore
   source brestore.gdb
end
document bbrestore
   restore breakpoints saved by bsave
end
```

```
#!/bin/sh
echo "set args 1" > ~/.gdbinit
export LD_LIBRARY_PATH=../
gdb ./a.out
```

