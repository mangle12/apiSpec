# K8S常用指令
###### tags: `k8s`

## 查看K8S狀態
:::info
kubectl get pods
:::
![](https://i.imgur.com/6p88Tfk.jpg)

## 查看單個POD的狀態
:::info
kubectl describe pod nlu-backend-POD後面一整串
:::
![](https://i.imgur.com/uBEGown.jpg)



## 查看K8S服務器狀況
:::info
kubectl l get svc
:::
![](https://i.imgur.com/xXc9r2k.jpg)


## K8S 砍掉 POD
kubectl delete pod [systalk-flow-editor-5d8fdddc77-fdxs5]

看LOG
:::info
kubectl logs -p [後面那一大串POD]
:::

