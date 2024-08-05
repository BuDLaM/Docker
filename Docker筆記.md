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
8. 
</name>
