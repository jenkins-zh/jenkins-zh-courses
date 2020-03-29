<!-- 为了方便命令的使用，首先启用命令的自动补全功能：`source <(jcli completion)`{{execute}} -->

通过下面的命令可以下载并启动一个 Jenkins:

`nohup jcli center start --context /jenkins --setup-wizard=false > jenkins.log 2>&1 &`{{execute}}

下面的命令可以查看 Jenkins 的启动日志的：

`tail -f jenkins.log`{{execute}}
