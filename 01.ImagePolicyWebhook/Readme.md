# ImagePolicyWebhook

官方文档：https://kubernetes.io/docs/reference/access-authn-authz/admission-controllers/#imagepolicywebhook

## 主要考察点

1、创建相对应的json或者yaml文件

2、启用 ImagePolicyWebhook （apiserver.yaml)
```yaml
- --enable-admission-plugins=NodeRestriction,ImagePolicyWebhook
```

3、指定准入控制器配置文件
```yaml
- --admission-control-config-file=/etc/kubernetes/epconfig/admission_configuration.json
```

4、mount
```yaml
# mount
    volumeMounts:
    - mountPath: /etc/kubernetes/epconfig
      name: epconfig
# 映射 volumes      
  volumes:
    - name: epconfig
    hostPath:
      path: /etc/kubernetes/epconfig
```

```shell
systemctl daemon-reload

systemctl restart kubelet
```