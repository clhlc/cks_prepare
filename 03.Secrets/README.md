# Secrets

Q:
1. 导出secret01的user和pass到对应的/etc/secret/user,和/etc/secret/pass
2. 新建secret02使用user和pass
3. 新建一个pod，pod01挂载新的secret02

A:
1. 
```shell
USER=$(kubectl get secrets secret1 -ojsonpath='{.data.user}'|base64 -d)
kubectl get secrets secret1 -ojsonpath='{.data.user}'|base64 -d > /etc/secret/user
```

```
PASS=$(kubectl get secrets secret1 -ojsonpath='{.data.pass}'|base64 -d)
kubectl get secrets secret1 -ojsonpath='{.data.pass}'|base64 -d > /etc/secret/pass
```

2. 
```
kubectl create secret generic secret2 --from-literal=user=$USER --from-literal=pass=$PASS
```

3. 创建pod挂载secret02
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mypod
spec:
  containers:
  - name: mypod
    image: redis
    volumeMounts:
    - name: foo
      mountPath: "/etc/foo"
      readOnly: true
  volumes:
  - name: foo
    secret:
      secretName: secret2
      optional: false # default setting; "mysecret" must exist
```