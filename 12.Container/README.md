# Containers

![12](../images/12.png)

## 删除有状态的和privileged的pod

## 1、删除有volume的pod

```shell
kubectl -n production get po xxx -o jsonpath={.spec.volumes} | jq
```

## 2、删除privilege为true的pod
```shell
kubectl -n production get po xxx -o yaml|grep "privilege"
```
