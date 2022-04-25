# API Server 认证

## 修改apiserver 启动安全加固
```yaml
- --authorization-mode=Node,RBAC 
- --enable-admission-plugins=NodeRestriction 
- --client-ca-file=/etc/kubernetes/pki/ca.crt 
- --enable-bootstrap-token-auth=true
- --anonymous-auth=false
```

## 删除system:anonymous的clusterrole
```shell

kubectl get clusterrolebinding system:anonymous
 
kubectl delete clusterrolebinding system:anonymous

```
