# PSP

官方文档：https://kubernetes.io/docs/concepts/policy/pod-security-policy/

## 创建新的psp

```shell
kubectl apply -f psp.yaml
```

## 创建clusterrole 使用psp

```shell

kubectl create sa sa01

kubect create clusterrole test-psp --verb use --resource psp

kubectl create clusterrolebinding test-psp --clusterrole test-psp --serviceaccount default:sa01

```
