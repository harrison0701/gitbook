# 安裝排除

[https://learn-k8s-from-scratch.readthedocs.io/en/latest/k8s-install/kubeadm.html](https://learn-k8s-from-scratch.readthedocs.io/en/latest/k8s-install/kubeadm.html)

这个错误表明 `/etc/apt/sources.list.d/docker.list` 文件的格式不正确。你需要修正这个文件。请按照以下步骤操作：

### 1. **检查和修复 Docker 仓库文件**

1.  **打开文件检查内容：**

    使用文本编辑器（比如 `nano` 或 `vim`）打开文件：

    ```bash
    bash複製程式碼
    sudo nano /etc/apt/sources.list.d/docker.list

    ```

    或者：

    ```bash
    bash複製程式碼
    sudo vim /etc/apt/sources.list.d/docker.list

    ```
2.  **修正文件内容：**

    确保文件内容是正确的，应该类似于以下格式：

    ```
    plaintext複製程式碼
    deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable

    ```

    如果 `$(lsb_release -cs)` 没有正确解析，你可以手动替换成你的 Ubuntu 版本代号，比如 `bionic`、`focal`、`jammy` 等。比如：

    ```
    plaintext複製程式碼
    deb [arch=amd64] https://download.docker.com/linux/ubuntu focal stable

    ```
3. **保存并关闭文件：**
   * 如果你使用 `nano`，按 `Ctrl+X`，然后按 `Y` 确认保存。
   * 如果你使用 `vim`，按 `Esc`，然后输入 `:wq` 并按 `Enter` 退出。

### 2. **更新 APT 包列表**

修正完文件后，更新 APT 包列表：

```bash
bash複製程式碼
sudo apt-get update

```

### 3. **检查是否有其他问题**

如果更新时仍然遇到问题，确保其他的 APT 源文件没有错误，可以检查 `/etc/apt/sources.list` 和 `/etc/apt/sources.list.d/` 目录下的其他文件。

直接跳到

```
mkdir -p $HOME/.kube
sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
sudo chown$(id -u):$(id -g) $HOME/.kube/config

//解決下面的問題
[root@node01 kubernetes]# mkdir ~/.kube
[root@node01 kubernetes]# cp /etc/kubernetes/kubelet.conf  ~/.kube/config

//預防這個錯誤
E0820 07:57:36.927551  985628 memcache.go:265] couldn't get current server API group list: Get "http://localhost:80
80/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
E0820 07:57:36.928256  985628 memcache.go:265] couldn't get current server API group list: Get "http://localhost:80
80/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
E0820 07:57:36.932952  985628 memcache.go:265] couldn't get current server API group list: Get "http://localhost:80
80/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
E0820 07:57:36.933943  985628 memcache.go:265] couldn't get current server API group list: Get "http://localhost:80
80/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused
E0820 07:57:36.935637  985628 memcache.go:265] couldn't get current server API group list: Get "http://localhost:80
80/api?timeout=32s": dial tcp [::1]:8080: connect: connection refused

```

```
kubectl get nodes

kubectl get pods -A

kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

kubectl get pods -A

curl -LO https://github.com/flannel-io/flannel/releases/download/v0.25.5/kube-flannel.yml

kubectl apply -f flannel.yaml

kubectl get pods -A
```
