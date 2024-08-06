<H2>Dokcer-Compose</H2>
需檢查是否有安裝Python

Compose的安裝
  - 安裝pip工具
    1. yum install -y epel-relase
    2. yum install -y python-pip
    3. pip install docker-compose==1.24.1
    4. 查看是否安裝成功: docker-compose version

> *安裝pip報錯*
> echo $?
> cd /etc/yum.repos.d/
> ls -lrt
> vi epel.repo
> ![image](https://github.com/user-attachments/assets/6ffee7b6-9e03-49f5-838e-f7d150cc5d4b)
> 刪掉#
    
  - 安裝docker-compose
