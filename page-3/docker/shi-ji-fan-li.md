# 實際範例

建立一個dockerfile 以建立nginx作範例

建立一個Dockerfile

```docker
FROM nginx:1.21.0-alpine

ADD index.html /usr/share/nginx/html/index.html
```

並輸入指令

```powershell
 docker image build -t mynginx-alpine .
```

此時會建立一個image 並在之後每次建立contaniner都會有index.html這個檔案

執行一個container(Centos)範例

```powershell
#-dt 的組合代表讓容器在後台運行（-d），並且同時分配一個終端（-t）。
docker run --name Mycentos -dt centos

#-it 顯示teminal並交互 bash顯示容器名稱
docker exec -it ddf1819eccbd21862f1b1b849a675273a796b67349612931e61add25fa527fa9 bash
```

docker run 注意事項

```docker
#不要使用多次run 會有太多分層 要講run都執行在一段
FROM ubuntu:20.04
RUN apt-get update && \
    apt-get install -y wget && \
    wget https://github.com/ipinfo/cli/releases/download/ipinfo-2.0.1/ipinfo_2.0.1_linux_amd64.tar.gz && \
    tar zxf ipinfo_2.0.1_linux_amd64.tar.gz && \
    mv ipinfo_2.0.1_linux_amd64 /usr/bin/ipinfo && \
    rm -rf ipinfo_2.0.1_linux_amd64.tar.gz
```
