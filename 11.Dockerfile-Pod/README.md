# Dockerfile Best Practices

官方文档：https://docs.docker.com/develop/develop-images/dockerfile_best-practices/

## Dockerfile
### 1. Dockerfile禁止使用root用户
```shell
USER nobody
```
### 2. image使用固定的tag
```shell
FROM ubuntu:16.04
```


## Pod、Deployment
### 1、修改特权
```yaml
privileged: flase
```
### 2、注意apiVersion

### 3、注意用户
```shell
runAsUser: 65535
```