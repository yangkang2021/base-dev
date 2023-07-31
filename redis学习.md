# Redis学习

## 一. 数据结构
![](.images/029e4e73.png)

## 二. 操作
```
INFO keyspace
SELECT 1 
ZCARD  newM3u8:xxx:source
zrevrangebyscore newM3u8:xxx:source +inf -inf WITHSCORES LIMIT 0 1
```