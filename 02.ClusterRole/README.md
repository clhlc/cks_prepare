# Clusterrole

修改namespace下role的权限只允许对某一类对象做list list的操作
新建一个serviceaccount (sa02)
创建名为role02的role，并且通过rolebinding绑定role02，只允许对persistentvolumeclaims做update操作。

```shell
1. 修改对应的role使用list权限

2. kubectl create sa sa01

3. kubectl create role role02 --verb=update

4. kubectl create rolebinding xxx-rolebinding --role role02 --serviceaccount namespace:sa02
```