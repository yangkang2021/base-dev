# linux硬盘读写测速
```
写入测试：

（1M数据大小，10k次写入）
dd if=/dev/zero of=/tmp/test bs=1M count=10k                        
dd if=/dev/zero of=/tmp/test bs=1M count=10k oflag=direct,nonblock
dd if=/dev/zero of=/tmp/test bs=1M count=10k oflag=dsync
dd if=/dev/zero of=/tmp/test bs=1M count=10k oflag=sync

读取测试：
（1M数据大小，10k次写入）
dd if=/dev/vda1 of=/dev/null bs=1M count=10k
dd if=/dev/vda1 of=/dev/null bs=1M count=10k iflag=direct,nonblock

读写测试：
（1M数据大小，10k次读写）
dd if=/dev/vda1 of=/tmp/test bs=1M count=10k
dd if=/dev/vda1 of=/tmp/test bs=1M count=10k iflag=direct,nonblock oflag=direct,nonblock

iops测试:
fio: https://blog.csdn.net/weixin_51697917/article/details/129552002

sudo fallocate -l 10G /mnt/testfile
sudo fio --filename=/mnt/testfile --direct=1 --rw=randwrite --bs=4k --ioengine=libaio --iodepth=64 --runtime=240 --numjobs=16 --time_based --group_reporting --name=4ktest
```