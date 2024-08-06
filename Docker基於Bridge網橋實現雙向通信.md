<H2>基於Bridge網橋實現雙向通信</H2>

CCS業務需求

創建網橋/網橋實戰:
1. dokcer network ls
2. docker network create -d bridge my_bridge
3. docker run -itd --name tomcat centos:7
4. docker run -itd --name redis centos:7
實現redis，tomcat，mysql雙向通信
5. docker netwrok connect my_bridge tomcat
6. docker netwrok connect my_bridge redis
驗證tomcat，redis網橋是否互通
7. docker exec -it redis /bin/bash
8. ping tomcat
9. docker exec -it tomcat /bin/bash
10. ping redis
