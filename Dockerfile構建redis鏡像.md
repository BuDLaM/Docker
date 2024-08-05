<h2>Dockerfile構建redis</h2>

Shell 腳本

```
#!/bin/bash
yum install -y gcc gcc-c++ make openssl openssl-devel
cd /home/redis-4.0.9
make && make PREFIX=/usr/local/redis install
mkdir -p /usr/local/redis/conf/
cp /home/redis-4.0.9/redis.conf /usr/local/redis/conf
```

手動啟動 

1. echo $?
2. cd /usr/local/redis/
3. ls -lrt
4. ls -lrt conf/
5. /usr/local/redis/bin/redis-server /usr/local/redis/conf/redis.conf

Dockerfile

```
FROM centos:7
ADD redis-4.0.9.tar.gz /home
COPY redis_install.sh /home
RUN sh /home/redis_install.sh
ENTRYPOINT /usr/local/redis/bin/redis-server /usr/local/redis/conf/redis.conf
```
