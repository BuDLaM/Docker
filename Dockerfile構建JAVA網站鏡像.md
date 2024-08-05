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
15. 
