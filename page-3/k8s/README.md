# K8s

筆記

[https://learn-k8s-from-scratch.readthedocs.io/en/latest/introduction.html](https://learn-k8s-from-scratch.readthedocs.io/en/latest/introduction.html)

kubectl get pods **取得 Kubernetes Cluster 中所有正在運行的 Pods 的資訊**

kubectl get pods _--show-all_ 如果加上`--show-all`，則會顯示所有 Pods

kubectl describe pod **取得某一個 Pod 的詳細資料**

kubectl expose pod --port= --name=**將某一 Pod 中指定的 port number expose 出來讓外部服務存取(建立一個新的 Service 物件)**

kubectl port-forward :**將某一 Pod 中指定的 port number mapping 到本機端的某一特定 port number**

kubectl attach -i **當一個 container 起來之後，有時希望能進到 container 內部去看 logs，可以使用 `kubectl attach` 這個指令**

kubectl exec -- **可以對 Pod 下一個內部指令**

kubectl label pods my-pod version=latest 我們想要`新增 labels`，可以輸入以下指令

kubectl get pods --show-labels 顯示標籤

安裝排除
