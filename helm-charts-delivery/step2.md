或者，通过 Jenkins CLI 来使用流水线的功能。

下载命令行 `curl -L https://github.com/jenkins-zh/jenkins-cli/releases/latest/download/jcli-linux-amd64.tar.gz|tar xzv`{{execute}}

添加环境变量：`echo export PATH=~:$PATH >> ~/.bashrc && source ~/.bashrc`{{execute}}

下载完成后，执行下面命令就可以看到所有的子命令：

`jcli`{{execute}}

在用户根目录下，增加 jcli 的配置文件：

`jcli config gen -i=false > ~/.jenkins-cli.yaml`{{execute}}

打开 Jenkins 的用户界面 `https://2886795314-30021-elsy04.environments.katacoda.com/user/admin/configure`{{execute}}

把生成的 Token 填入到客户端的配置文件中 `jcli config edit`：
