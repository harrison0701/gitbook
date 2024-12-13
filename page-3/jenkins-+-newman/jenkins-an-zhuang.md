# jenkins安裝

Jenkins for windows

照流程裝

[https://medium.com/on-my-way-coding/初探ci工具-jenkins-windows環境安裝-81765fee3532](https://medium.com/on-my-way-coding/%E5%88%9D%E6%8E%A2ci%E5%B7%A5%E5%85%B7-jenkins-windows%E7%92%B0%E5%A2%83%E5%AE%89%E8%A3%9D-81765fee3532)

設定本機安裝性原則

控制台>>>系統及安全性>>>系統管理工具>>>本機安裝性原則(點兩下)

本機原則>>>使用者權限指派>>>以服務方式登入(點兩下)

輸入登入帳號(白色大格子)>>>檢查>>>確認

安裝Java 11

產生證書給iis使用

New-SelfSignedCertificate –DnsName [jbpublish.eastasia.cloudapp.azure.com](http://jbpublish.eastasia.cloudapp.azure.com/) -CertStoreLocation "cert:\LocalMachine\My"

安裝git

[https://git-scm.com/download/win](https://git-scm.com/download/win)

安裝dotnet

[https://learn.microsoft.com/zh-tw/dotnet/core/install/windows?tabs=net70](https://learn.microsoft.com/zh-tw/dotnet/core/install/windows?tabs=net70)

安裝SDK才可以執行dotnet build

runtime不一定要安裝

最後再安裝主執行檔

主執行程式(左邊找windows版本)

[https://www.jenkins.io/download/#downloading-jenkins](https://www.jenkins.io/download/#downloading-jenkins)

jenkins安裝必要外掛

NuGet,MSBuild

[https://blog.yowko.com/jenkins-build-dotnet-project/](https://blog.yowko.com/jenkins-build-dotnet-project/)

環境變數

[http://jbpublish.eastasia.cloudapp.azure.com:8080/env-vars.html/](http://jbpublish.eastasia.cloudapp.azure.com:8080/env-vars.html/)

編碼改變(這樣才不會出現亂碼)

[https://blog.miniasp.com/post/2015/12/24/Jenkins-on-Windows-03-Avoid-messy-words-in-log-messages](https://blog.miniasp.com/post/2015/12/24/Jenkins-on-Windows-03-Avoid-messy-words-in-log-messages)

SETX /M JAVA\_TOOL\_OPTIONS -Dfile.encoding=UTF8
