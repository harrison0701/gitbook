# Jenkins + newman

[https://blog.yowko.com/jenkins-postman/](https://blog.yowko.com/jenkins-postman/)

要先匯出postman環境跟資料夾

假如是linux環境要裝node.js npm

```powershell
apt update
apt install nodejs 
apt install npm
npm install -g newman
```

建立pineline

newman run {collection path} -e {environment path}

docker 裝jenkins

docker run --name jenkins -d --restart always -p 8080:8080 -p 50000:50000 -v /data/jenkins:/var/jenkins\_home -v /var/run/docker.sock:/var/run/docker.sock jenkins/jenkins

取密碼

docker exec -it jenkins cat /var/jenkins\_home/secrets/initialAdminPassword

jenkins安裝
