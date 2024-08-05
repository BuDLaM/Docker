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
