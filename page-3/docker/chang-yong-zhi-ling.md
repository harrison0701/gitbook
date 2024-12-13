# 常用指令

常用指令

docker version — 查看版本

docker run -it ubuntu /bin/bash 開啟新的容器

docker container run nginx - 創建新的容器

docker container ps-a - 查看運行中的虛擬機

docker rm - 刪除指定虛擬機

docker container stop 暫停指定虛擬機

docker container ps-aq 印出所有Id

docker container stop $(docker container ps -aq) 暫停所有印出的Id(適用rm)

docker exec -u root -it \<container\_id\_or\_name> sh (/bin/bash)以root身分進入bash

docker attach 監控

docker Container logs

//image鏡像檔

docker image pull nginx(可替換docker hub的鏡像)

docker image ls 查看所有鏡像列表

docker pull nginx:1.25.0 //可以拉取想要的Tag

docker image rm 7d(編號)

docker image save nginx -o nginx.image 導出

2024/03/05

docker image tag nginx jbharrison0701/hello:1.0 複製一個相同的image 以及給他新的tag(預設是lastest)

docker image push jbharrison0701/hello:1.0 將一個image放到hub jbharrison0701為前綴 要跟hub名字相同

docker image history 47ay查看檔案分層

docker image build -f dockerfile.good.txt -t ipinfo-good . 使用這個txt創建一個映像

2024/03/19

docker image build -f .\Dockerfile-arg.dockerfile -t ipinfo-arg . 使用dockerfile建置新的image 使用同資料夾下檔案建置

2024/04/19

docker system prune -f 刪除已經停止的容器
