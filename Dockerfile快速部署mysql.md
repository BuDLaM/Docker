<h2>Dockerfile部署mysql數據庫</h2>

1. docker pull mysql:5.7
2. docker images
3. Docker啟動mysql數據庫 (參考:hub.docker.com/_/mysql)
   - docker run --name some-mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:5.7
4. docker ps
5. docker exec -it mycentos:mysql /bin/bash
6. mysql -uroot -pmy-secret-pw
7. 創建mysql庫

![image](https://github.com/user-attachments/assets/2714a18f-758c-4873-b68a-213c9dc71822)

查看字符節
8. locale
9. docker rm -f centos:mysql
10. docker run --name some-mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=my-secret-pw -d mysql:5.7
11. docker exec -it mycentos:sql env LANG=C.UTF-8 /bin/bash
12. echo $LANG
13. mysql -uroot -pmy-secret-pw
14. 驗證(自行驗證)
15. docker rm -f $(docker ps -a -q)
16. ls -lrt
17. cat > init.sql > 輸入圖片內容
18. cat > dockerfile > 輸入以下dockerfile內容
19. docker build -t mysql:5.7 .
20. docker ps 
21. docker run --name some-mysql -p 3307:3306 -e MYSQL_ROOT_PASSWORD=abc12345678 -d my-mysql:5.7
22. docker exec -it mysql /bin/bash
23. ls -lrt




dockerfile

```
FROM mysql:5.7
WORKDIR /docker-entrypoint-initdb.d
ENV LANG=C.UTF-8
ADD init.sql . (ADD執行語句, COPY不會)
```
