[ChartMuseum](https://github.com/helm/chartmuseum) 是 Helm Chart 的仓库，在本次教程中，会把构建出来的 Chart 上传上去。

首先，通过下面的命令来安装 `ChartMuseum`：

```
helm install chartmuseum stable/chartmuseum \
    --set service.type=NodePort \
    --set service.nodePort=32132 \
    --set env.open.DISABLE_API="false"
```{{execute}}

查看是否启动：`kubectl get pod | grep chartmuseum`{{execute}}

访问地址为 `https://[[HOST_SUBDOMAIN]]-30021-[[KATACODA_HOST]].environments.katacoda.com/`
