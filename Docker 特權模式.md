<h2>Docker特權模式</h2>

普通模式下刪除default gw實驗
1. docker run -itd --name mycentos centos:7 /bin/bash
2. docker exec -it ef /bin/bash
3. route -n
4. yum install -y net-tools
5. route -n
6. route del default gw 127.0.0.1
7. id
開啟特權模式
8. docker run -itd --privileged=tru --name mycentos1 centos:7
9. docker exec -it mycentos1 /bin/bash
10. yum install -y net-tools
11. route -n
12. route del default gw 127.0.0.1
