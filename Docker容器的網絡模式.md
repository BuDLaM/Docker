<h2>Docker網絡模式</h2>

- 默認的三種網絡模式:
  1. bridge: 橋接模式 (默認模式)
     - docker0虛擬網橋
    
     - 安裝工具:
       1. yum -y install net-tools
       2. yum install -y bridge-utils >  brctl show (查看網卡橋接狀態)


  2. host: 主機模式
     - 容器不再擁有自己的IP地址，而是使用宿主機的IP地址和端口
    
      修改為主機模式: docker run -itd --net=host mycentos:nginx /usr/local/nginx/sbin/nginx  -g "daemon off;"

  3. none: 無網絡模式
 
> 查看網絡模式
> docker network ls


![image](https://github.com/user-attachments/assets/ad4e3a19-3d72-4ac6-be8d-6120313c6780)
