<H2>Dockerfile基礎指令</H2>

命令格式:
- shell命令格式: RUN yum install -y net-tools
- exec命令格式: RUN ["yum","install","-y","net-tools"]

1. FORM: 基於那個鏡像
2. MAINTAINER: 注明作者
4. COPY: 複製文件進入鏡像 (只能用相對路徑, 不能使用絕對路徑)
5. ADD: 複製文件進入鏡像 (如文件為.tar .gz會自動解壓文件)
6. WORKDIR: 指定工作目錄，假如路徑不存在會創建路徑
7. ENV: 設置環境變量
8. EXPOSE: 暴露容器端口
9. RUN: 作用在鏡像層
   - 在構建鏡像的時候執行，作用於鏡像層
11. ENTRYPOINT: 作用在容器層
   - 在容器啟動的時候執行，作用於容器層，Dockerfile里有多條時只允許執行最後一條
13. CMD: 作用在容器層，可覆蓋
   - 在容器啟動的時候執行，作用於容器層，Dorkerfile里有多條時只允許執行最後一條
   - 容器啟動後執行默認的命令或參數，允許被修改


![image](https://github.com/user-attachments/assets/7937a749-3fde-4c1c-9909-474c1fcc3ecc)



![image](https://github.com/user-attachments/assets/bdabae74-16be-4eae-8844-e641422ec6f4)

![image](https://github.com/user-attachments/assets/7f4267ee-de0a-434e-8696-8c3ddab85252)

![image](https://github.com/user-attachments/assets/b434069c-850a-49af-9638-39afde49f6d8)

