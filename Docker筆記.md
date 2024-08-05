<h2>安裝環境</h2>

1. 安裝環境: Centos 7
2. 安裝條件: Linux 3.8及以上
3. Docker 版本:
   - Docker EE 企業版本
   - Docker CE 社區版本
  
4. 關閉防火牆: systemctl stop firewalld.service > vi/etc/selinux/config
5. 安裝Docker CE社區版
6. 安裝wget命令
7. 下載阿里云Docker社區版VUM源
   - cd /etc/yum.repos.d/
   - wget http://mirrors.aliyun.com/docker-ce/linux/centos/docker-ce.repo

8. 查看Docker安裝包: yum list | grep docker
9. 安裝Docker CE社區版本: yum install -y docker-ce.x86-64
10. 設置開機啟動: systemctl enable docker
11. 更新xfsprogs: yum -y update xfsprogs
12. 啟動Docker: systemctl start docker
13. 查看版本: docker version
