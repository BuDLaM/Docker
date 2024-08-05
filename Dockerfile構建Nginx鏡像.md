<h2>Dockerfile構建Nginx</h2>

安裝Nginx的Shell腳本

```
#!/bin/bash
yum install -y gcc-c++ make pcre pcre-devel zlib zlib-devel
cd /usr/local/nginx-1.16.0
./configure --prefix=/usr/local/nginx && make && make install
rm -rf /home/nginx-1.16.0 (可不用加，dockerfile會自動刪除) 
```

Dockerfile
```
FROM centos:7
ADD nginx-1.16.0.tar.gz /usr/local
COPY nginx_install.sh /usr/local
RUN sh /usr/local/nginx_install.sh
EXPOSR 80
```

1. dokcer build -t mycentos:nginx .
2. docker run -itd -p 80:80 mycentos:nginx /usr/local/nginx/sbin/nginx -g "daemon off;" (前台啟動:-g "daemon off;")
3. 
