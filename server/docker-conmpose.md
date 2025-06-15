


## 参考
mysql redis ：https://blog.csdn.net/qq_40298351/article/details/140994072
docker compose命令: https://blog.csdn.net/justlpf/article/details/132734556

docker compose up -d
docker compose down


├── compose.yml
├── mysql
│   ├── conf
│   ├── data
│   └── log
└── redis
    ├── conf
    ├── data
    └── log

启动出错：
查看日志：docker logs <container_id_or_name>