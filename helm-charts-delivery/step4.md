[ChartMuseum](https://github.com/helm/chartmuseum) 是 Helm Chart 的仓库，在本次教程中，会把构建出来的 Chart 上传上去。
通过下面的命令来安装：

```
helm install chartmuseum stable/chartmuseum \
    --set service.type=NodePort \
    --set service.nodePort=32132 \
    --set env.open.DISABLE_API="false"
```{{execute}}