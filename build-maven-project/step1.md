#### 启动 Jenkins
使用如下命令启动 Jenkins 容器：

`docker run -d --name jenkins \
    -p 8080:8080 -p 50000:50000 \
    --env JAVA_OPTS="-Djenkins.install.runSetupWizard=false" \
    jenkinszh/jenkins-pipeline:2.223`{{execute}}

相关插件（git、pipeline）和工具（Maven）已经预先配置好；
8080 端口用来打开 web dashboard，50000 端口用来和其它 Jenkins agent 通信。

#### 打开 Dashboard

你可以通过下面 URL 打开 Jenkins Dashboard：https://[[HOST_SUBDOMAIN]]-8080-[[KATACODA_HOST]].environments.katacoda.com/

Jenkins 可能需要一点时间来完成启动并准备就绪，在接下来的步骤中，您将使用 Dashboard 开始构建 Maven 项目。
