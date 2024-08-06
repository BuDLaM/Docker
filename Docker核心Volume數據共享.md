<h2>Volume 介紹使用 </h2>

Dockerfile

```
FROM centos:7
VOLUME["/usr/local"]
```

1. cat > dockerfile > 輸入Dockerfile內容
2. docker build -t centos:v1
3. docker images
4. docker run -itd --name centos7 centos:v1 /bin/bash
5. docker inspect centos7 > Mount > Destination
6. copy "Source"
7. cd "Source"
8. ls -lrt

實戰
1. cd /usr/local/
2. cd nginx/
3. ls -lrt
4. cd html/
5. ls -rlt
6. cd ..
7. ps -ef | grep nginx
8. /usr/local/nginx/sbin/nginx
9. ps -ef | grep nginx
10. cd nginx/
11. ls -lrt
12. cd html
13. ls -lrt
14. cat > index.html > this is docker!!!
15. cat index.html
16. pwd
17. docker run -itd -p 8080:80 -v /usr/local/nginx/html:/usr/local/nginx/html --name nginx1 mycentos:nginx /usr/local/nginx/sbin/nginx -g "daemon off;"
18. website: host IP:8080
19. docker run -itd -p 8081:80 --volumes-from nginx1 --name nginx2 mycentos:nginx /usr/local/nginx/sbin/nginx -g "daemon off;"
20. docker inspect nginx2
21. docker run -itd -p 8082:80 --volumes-from nginx1 --name nginx3 mycentos:nginx /usr/local/nginx/sbin/nginx -g "daemon off;"
