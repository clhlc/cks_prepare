# kube-bench

![10](../images/10.png)

1、在api server的配置文件修改：

--authorization-mode=Node,RBAC

2、kubelet
```yaml
address: 0.0.0.0
apiVersion: kubelet.config.k8s.io/v1beta1
authentication:
  anonymous:
    enabled: false # 修改为false
  webhook:
    cacheTTL: 2m0s
    enabled: true
  x509:
    clientCAFile: /etc/kubernetes/pki/ca.crt
authorization:
  mode: Webhook # 修改为Webhook
  webhook:
    cacheAuthorizedTTL: 5m0s
    cacheUnauthorizedTTL: 30s
...
```

3、etcd.yaml

--client-cert-auth=true