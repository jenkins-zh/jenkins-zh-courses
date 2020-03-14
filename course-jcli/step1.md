Linux 下的用户，可以通过下面的命令下载最新版本的 `jcli`

`curl -L https://github.com/jenkins-zh/jenkins-cli/releases/latest/download/jcli-linux-amd64.tar.gz|tar xzv`{{execute}}

添加环境变量：`echo export PATH=~:$PATH >> ~/.bashrc && source ~/.bashrc`{{execute}}

下载完成后，执行下面命令就可以看到所有的子命令：

`jcli`{{execute}}
