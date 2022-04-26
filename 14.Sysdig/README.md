# Sysdig

![14](../images/14.png)

Make sure to store the incident file on the cluster's worker node.


## 登录到pod所在的node节点，并且查看对应pod的container id

```shell
# 查看sysdig支持类型
sysdig -l |grep -iE 'time|user|proc'

# 查看tomcat容器id
docker ps|grep tomcat

# node节点执行命令
sysdig -M 30 -p "%evt.time,%user.uid,%proc.name" container.id=[container_id] > /opt/KSRS00101/incidents/summary
```