<H2>Dokcer-Compose</H2>
需檢查是否有安裝Python

Compose的安裝
  - 安裝pip工具
    yum install -y python-pip 安裝不了跳下再安裝
    yum install -y epel-relase

> 安裝還是失敗
> echo $?
> cd /etc/yum.repos.d/
> ls -lrt
> vi epel.repo
> ![image](https://github.com/user-attachments/assets/6ffee7b6-9e03-49f5-838e-f7d150cc5d4b)
> 刪掉#
    
  - 安裝docker-compose
