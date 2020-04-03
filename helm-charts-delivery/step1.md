首先，安装 [Helm3](https://helm.sh/)，准备后面安装 Jenkins Chart：

```
wget https://get.helm.sh/helm-v3.1.0-linux-amd64.tar.gz
tar xzvf helm-v3.1.0-linux-amd64.tar.gz
cp linux-amd64/helm $(which helm)
```{{execute}}

Kubernetes 的启动，可能需要花费一些时间，执行下面的命令，如果成功返回了命名空间列表的话，说明 Kubernetes 是否启动成功

`kubectl get ns`{{execute}}

然后，安装由中文社区维护的定制版本的 Jenkins：
```
helm repo add stable https://kubernetes-charts.storage.googleapis.com
helm install jenkins stable/jenkins \
    --set master.image=jenkinszh/jenkins-k8s \
    --set master.tag=2.222.1 \
    --set master.imagePullPolicy=IfNotPresent \
    --set persistence.enabled=false \
    --set master.nodePort=30021 \
    --set master.serviceType=NodePort
```{{execute}}

等待 Jenkins 启动：`kubectl get pod -w`{{execute}}

通过下面的命令，查看 Jenkins 用户 `admin` 的密码：
```
printf $(kubectl get secret --namespace default jenkins -o jsonpath="{.data.jenkins-admin-password}" | base64 --decode);echo
```{{execute}}

我们可以打开 Jenkins 的管理界面，https://[[HOST_SUBDOMAIN]]-30021-[[KATACODA_HOST]].environments.katacoda.com/
