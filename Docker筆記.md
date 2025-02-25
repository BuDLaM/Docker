<h2>安裝環境</h2>

1. 安裝環境: Centos 7
2. 安裝條件: Linux 3.8及以上
3. Docker 版本:
   - Docker EE 企業版本
   - Docker CE 社區版本
  
4. 關閉防火牆: systemctl stop firewalld.service > vi/etc/selinux/config > SELINUX=enforce > SELINUX=disable
5. 安裝Docker CE社區版
6. 安裝wget命令: yum install -y wget
7. 下載阿里云Docker社區版VUM源
   - cd /etc/yum.repos.d/
   - wget http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

8. 查所有Docker版本安裝包: yum list | grep docker
9. 安裝Docker CE社區版本: yum install -y docker-ce.x86-64
10. 設置開機啟動: systemctl enable docker
11. 更新xfsprogs: yum -y update xfsprogs
12. 啟動Docker: systemctl start docker
13. 查看版本: docker version
14. 查看詳細信息: docker info

<H2>Docker 鏡像實戰 </H2>

1. 查看Docker本地鏡像: docker images
2. 搜索鏡像: docker search centos
3. 搜索官方鏡像: docker search --filter "is-official=true" centos
4. 搜索>10顆星的鏡像: docker search --filter stars=10 centos
5. 下載Centos 7本地鏡像: docker pull centos:7
6. 修改本地鏡像名字(小寫): docker tag centos:7 mycentos:1
7. 刪除本地鏡像: docker rmi <name>

<H2>Docker 國內阿里云鏡像加速</H2>

1. 登錄阿里云 > 控制台
2. 左上角 > 產品與服務 > 搜索: 容器
3. 選和器鏡像服務 > 鏡像加速器 
4. 加速器地址 > 操作文檔 > Centos
5. Copy > paste

<H2>Docker容器構建基本操作</H2>

1. 啟動容器: docker run -it/itd centos:7
   - -i: 表示以交互模式運行容器(讓容器的標準輸入保持打開)
   - -d: 表示後台運行容器，并返回容器ID，並啟動
   - -t :為容器重新分配一個偽輸入終端
   - --name: 為容器指定名稱
2. 查看本地所有容器: docker images
3. 查看本地正在運行的容器: docker ps -a
4. 停止容器: docker stop <name>
5. 一次性停止所有容器: docker stop $(docker ps -a -q)
6. 啟動容器: docker start <name> 
7. 重啟容器: docker restart <name>
8. 刪除容器: docker rm <name> 
9. 強制刪除鏡像: docker rm -f <name>
10. 查看容器詳細信息: docker inspect <name>
11. 進入容器:docker -it exec <name> /bin/bash

<H2>Docker容器的文件複製和掛載</H2> 

1. 從宿主機複製到容器: docker cp 宿主機本地路徑 容器名字:容器路徑
   - docker cp /root/123.txt mycentos:/home/
2. 從容器複製到宿主機: docker cp 容器名字:容器路徑 宿主機本地路徑
   - docker cp mycentos:/home/123.txt /root
3. 宿主機文件掛載(文件自動同步)到容器裡:  (啟動中的容器無法掛載)
   - mkdir xdclass
   - docker run -itd -v /root/xdclass/:/home centos:7 (-v 掛載)
   
<H2>Docker自定義鏡像</H2>

1. Docker目前鏡像制作方法:
   - 基於Docker Commit制作鏡像
   - 基於DockerFile制作鏡像，Dockefile方式為主流的制作鏡像方式

2. 修改容器以及保存容器
   - 啟動并進入容器
     1. docker run -it centos:7 /bin/bash
     2. cd /home/
     3. mkdir xdclass
     4. ifconfig (沒有內容)
     5. yum install -y net-tools
     6. ifconfig (有內容)
     7. exit
     8. docker commit -a <作者> -m <描述> <現有容器> <新版本容器>
        - docker commit -a "XD" -m "mkdir /home/xdclass" <container id> mycentos:v1

<h2>Docker構建鏡像</h2>

Dockerfile構建鏡像實戰
1. Dockerfile

```
# this is a dockerfile
FROM centos:7
MAINTAINER XD 12345@qq.com (指名作者 郵箱)
RUN echo "正在構建鏡像"
WORKDIR /home/xdclass
COPY 123.txt /home/xdclass (絕對路徑, 123.txt路徑放在Dockerfile路徑裡)
RUN yum install -y net-tools
```

Linux:
1. cd ~
2. vi dockerfile
3. paste dockerfile 內容
4. 123.txt 要和 dockerfile 路徑一致
5. 構建: docker build -t mycentos:v2
6. 查看: docker images
7. 驗證: 進入驗證
