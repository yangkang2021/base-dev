# KCP
> https://github.com/xtaci/kcp-go

1. IKCP_RTO_MIN     = 10
3. convid
4. conn.SetNoDelay(1, 10, 2, 1)
5. conn.SetWindowSize(128, 128)
6. kcp内部分包：24+1376，最多256片