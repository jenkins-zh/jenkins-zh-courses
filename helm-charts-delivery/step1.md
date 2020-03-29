首先，我们安装由中文社区维护的定制版本的 Jenkins：

```
helm repo add stable https://kubernetes-charts.storage.googleapis.com
helm install jenkins stable/jenkins \
    --set master.image=jenkinszh/jenkins-k8s \
    --set master.tag=2.204.5 \
    --set master.imagePullPolicy=IfNotPresent \
    --set persistence.enabled=false \
    --set master.serviceType=NodePort
```{{execute}}
