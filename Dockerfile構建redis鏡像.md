<h2>Dockerfile構建redis</h2>

Shell 腳本安裝redis

```
#!/bin/bash
yum install -y gcc gcc-c++ make openssl openssl-devel
cd /home/redis-4.0.9
make && make PREFIX=/usr/local/redis install
mkdir -p /usr/local/redis/conf/
cp /home/redis-4.0.9/redis.conf /usr/local/redis/conf
通過命令修改配置文件
sed -i '69s/127.0.0.1/0.0.0.0/' /usr/local/redis/conf/redis.conf
sed -i '88s/protected-mode yes/protected-mode no' /usr/local/redis/conf/redis.conf
```

手動啟動Redis

```
1. echo $?
2. cd /usr/local/redis/
3. ls -lrt
4. ls -lrt conf/
5. /usr/local/redis/bin/redis-server /usr/local/redis/conf/redis.conf
```

Dockerfile

```
FROM centos:7
ADD redis-4.0.9.tar.gz /home
COPY redis_install.sh /home
RUN sh /home/redis_install.sh
ENTRYPOINT /usr/local/redis/bin/redis-server /usr/local/redis/conf/redis.conf
```

1. docker build -t mycentos:redis .
2. docker images
3. docker run -itd mycentos:redis
4. docker ps
5. docker exec -it mycentos:redis /bin/bash
6. ps -ef | grep redis
7. /usr/local/redis/bin/redis-cli (進入redis客戶端驗證)
8. set name xdclass
9. get name
10. exit
11. exit
12. docker run -itd -p 6380:6379 mycentos:redis
13. docker ps
14. /usr/local/redis/bin/redis-cli -p 6380
15. set name xdclass > failed
16. docker exec -it mycentos:reids /bin/bash
17. vi /usr/local/redis/conf/redis.conf  > protected-mode yes > protected-mode no > bind 127.0.0.1 > #bind 127.0.0.1
18. docker restart mycentos:redis
19. /usr/local/redis/bin/redis-cli -p 6380
20. set name xdclass
21. get name
通過IP地址連接:
22. docker inspect mycentos:redis > NetworkSetting > "IPAddress"
23. /usr/local/redis/bin/redis-cli -h xxx.xxx.xxx.xxx 6379
24. set name okok
25. get name 
