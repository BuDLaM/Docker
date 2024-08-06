<h2>Docker網絡模式</h2>

- 默認的三種網絡模式:
  1. bridge: 橋接模式
     - docker0虛擬網橋
    
     - 安裝工具:
       1. yum -y install net-tools
       2. yum install -y bridge-utils >  brctl show (查看網卡橋接狀態)
 
![image](https://github.com/user-attachments/assets/0ca717e3-48f7-448b-9e95-2813709fc06b)

  2. host: 主機模式
  3. none: 無網絡模式
 
> 查看網絡模式
> docker network ls
