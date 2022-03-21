# Service account

官方文档: https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/

## 1. 创建service account，不自动挂载token

### service account

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: frontend-sa
  namespace： qa
automountServiceAccountToken: false # *
```

### pod
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-pod
  namespace: qa 
spec:
  serviceAccountName: frontend-sa
  automountServiceAccountToken: false # *
```

## 2. 删除没有使用的service account

```shell
kubectl get po -oyaml|grep -i serviceaccountname

kubectl get sa

对比后删除没有使用的service account
```