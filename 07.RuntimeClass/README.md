# Runtime Class

![](../images/7.png)
## 创建Runtime Class
```yaml
apiVersion: node.k8s.io/v1
kind: RuntimeClass
metadata:
  name: untrusted
handler: runsc
```
## 更新Pod中使用新的Runtime Class (handler)
```shell
kubectl get all -n server
```

```yaml
spec:
  runtimeClassName: untrusted   
  containers:
```