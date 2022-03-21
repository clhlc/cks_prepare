# Trivy


## 找出镜像中critical和high的镜像，并且删除对应的pod

```shel
kubectl get po -o yaml|grep 'image: '
```

```shell
trivy image -s CRITICAL,HIGH nginx:latest
```

```shell
kubectl delete po xxx
```