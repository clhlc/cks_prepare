# Sysdig

![14](../images/14.png)

Make sure to store the incident file on the cluster's worker node.


## 登录到pod所在的node节点，并且查看对应pod的container id

```shell
sysdig -M 30 -p "%evt.time,%user.uid,%proc.name" container.id=[container_id] > /opt/KSRS00101/incidents/summary
```