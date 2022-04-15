# AppArmor

![5](../images/5.png)

## 官方文档：https://kubernetes.io/docs/tutorials/security/apparmor/


## 在node节点创建AppArmor使用的profile,并加载profile 文件

```shell
apparmor_parser profile
```

## 创建pod

```shell
kubectl apply -f pod.yaml
```