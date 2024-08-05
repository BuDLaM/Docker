<h2>Dockerfile 構建JAVA環境</h2>

本地宿主機配置jdk

```
export JAVA_HOME=/usr/local/jdk < 需修改路徑位置
export JRE_HOME=$JAVA_HOME/jre
export CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
export PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
```

1. 解壓JDK/Tomcat文件包: tar -xf jdk-8u211-linux-x64.tar.gz / tar -xf apache-tomcat-8.5.35.tar.gz
2. ls -lrt
3. 移動安裝包JDK (不規定): mv jdk1.8.0_211 /usr/local/jdk
4. cd /usr/local
5. ls -rlt jdk
6. vi /etc/profile > 插入上面內容到文檔最下
7. 加載變量: source /etc/profile
8. java -version (出現以下內容為成功加載JAVA環境)

![image](https://github.com/user-attachments/assets/ce39f67a-26c9-44b2-9ae3-d9ef5993beef)

9. 移動安裝包 Tomcat (不規定): mv apache-tomcat-8.5.35 /usr/local/tomcat
10. cd /usr/local/tomcat
11. ls -lrt
12. cd bin
13. ls -lrt
14. ./startup.sh
15. website: http://xxx.xxx.xxx.xxx:8080
16. 如無法進入關閉防火牆: systemctl stop firewalld.service
17. 查看防火牆: firewall-cmd --state

```
關閉tomcat
1. pkill tomcat / kill xxxxx
2. ps -ef | grep tomcat (查看xxxxx)
```

<h2>Dockerfile配置</h2>

```
FROM centos:7
ADD jdk-8u211-linux-x64.tar.gz /usr/local
RUN mv /usr/local/jdk1.8.0_211 /usr/local/jdk
ENV JAVA_HOME=/usr/local/jdk
ENV JRE_HOME=$JAVA_HOME/jre
ENV CLASSPATH=$JAVA_HOME/lib:$JRE_HOME/lib:$CLASSPATH
ENV PATH=$JAVA_HOME/bin:$JRE_HOME/bin:$PATH
ADD apache-tomcat-8.5.35.tar.gz /usr/local
RUN mv /usr/local/apache-tomcat-8.5.35 /usr/local/tomcat
EXPOSE 8080
ENTRYPOINT ["/usr/local/tomcat/bin/catalina.sh","run"]
```

1. 在相同目錄下創建Dockerfile
2. 貼上以上文本
3. 創建容器: docker build -t mycentos:jdk .
4. 啟動容器: docker run -itd -p 80:8080 mycentos:jdk /bin/bash

掛載方法:

4. mkdir ROOT
5. ls -lrt
6. cd ROOT/
7. pwd
8. docker run -itd -p 80:8080 -v /root/test/ROOT:/usr/local/tomcat/webapps/ROOT /root/test/ROOT
9. 驗證: ls -lrt > vi index.html > Hello World

防火牆報錯: 

![image](https://github.com/user-attachments/assets/577efd5b-4d99-4a74-a93c-8f2cfffb1635)

1. systemctl start firewalld.service
2. docker ps
3. website: http:xxx.xxx.xxx.xxxx:80
