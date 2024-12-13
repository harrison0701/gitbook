# 錯誤排除

想要打开之前使用过的一个容器，却出现以下错误提示

Error invoking remote method 'docker-start-container': Error: (HTTP code 500) server error - Ports are not available: listen tcp 0.0.0.0:8787: bind: An attempt was made to access a socket in a way forbidden by its access permissions.

百度到的方法没有解决，比如重启系统和docker，或查看端口占用情况等

请教了朋友，解决需要先关闭Windows NAT服务

net stop winnat docker start container\_name net start winnat

执行以上可正常使用了，在此记录

经使用，不必每次执行以上步骤

如果遇到緩存的情況

當你在 Dockerfile 中使用 `ADD` 或 `COPY` 指令將檔案加入到映像檔時，Docker 會嘗試使用先前的緩存來加快建置速度。這就是為什麼即使你更新了檔案，Docker 仍然可能會使用先前緩存的檔案來進行建置，而不是使用你最新的檔案。

這種情況發生的原因通常是 Docker 的 **分層建置機制**。每個 `RUN`、`ADD`、`COPY` 等指令都會建立一個新的層，如果該層的輸入（例如，檔案的路徑、內容等）與之前相同，Docker 會認為該層沒有改變，並且從緩存中取用它。

### 解決方法：

1.  **強制不使用緩存**：使用 `-no-cache` 參數，讓 Docker 完全忽略緩存並重新建置所有層。

    ```bash
    bash
    複製程式碼
    docker build --no-cache -t <映像名稱>:<標籤> .

    ```
2. **檢查 Dockerfile 的建置順序**：如果 `ADD` 或 `COPY` 指令在 Dockerfile 中的位置靠後，並且之前的指令沒改變，Docker 可能會使用緩存。你可以確保修改檔案的動作發生在合適的位置，讓 Docker 知道它需要重新執行該步驟。
3. **修改檔案的時間戳**：有時 Docker 檢查檔案的變化是基於時間戳。如果檔案內容更新，但時間戳沒有變化，Docker 可能認為檔案沒有變。你可以確保檔案有新的時間戳，或在檔案有變動後使用 `touch` 命令更新檔案的時間戳。

### 範例：

```
Dockerfile
複製程式碼
# 假設你在 Dockerfile 使用以下指令來加入本地檔案到映像檔
ADD ./app /usr/src/app

# 如果 app 目錄或其中文件沒有變化，Docker 會從緩存取用

```

要確保 Docker 使用新版本的檔案：

1. 使用 `-no-cache` 建置映像。
2. 確保檔案的變動已正確更新並反映在時間戳上。

這樣可以防止 Docker 使用舊的緩存檔案。
