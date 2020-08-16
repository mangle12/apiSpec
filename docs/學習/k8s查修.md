# k8s 查修

## 狀況排除

### 查K8S運作狀況
```linux
kubectl get pods -n kube-system
```

### 查看k8s狀況
```linux
watch kubectl get pods
kubectl get pods
```

### 執行 mongo import
kubectl create job --from=cronjob/report-mongo-importer report-mongo-importer-20200811001
kubectl delete job <>
kubectl logs <>