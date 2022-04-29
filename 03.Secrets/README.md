# Secrets

![](../images/3.png)

## 1、导出存在的secret
```shell
kubectl -n istio-system get secrets db1-test -ojsonpath='{.data.user}'|base64 -d > /etc/candidate/user.txt

kubectl -n istio-system get secrets db1-test -ojsonpath='{.data.pass}'|base64 -d > /etc/candidate/pass.txt
```

## 2、新建secret
```
kubectl create secret generic db2-test --from-literal=user=production-instance --from-literal=pass=password -n istio-system
```

## 3、创建pod挂载secret
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: secret-pod
  namespace: istio-system
spec:
  containers:
  - name: dev-container
    image: nginx
    volumeMounts:
    - name: secret-volume
      mountPath: "/etc/secret"
      readOnly: true
  volumes:
  - name: secret-volume
    secret:
      secretName: db2-test
      optional: false # default setting; "mysecret" must exist
```