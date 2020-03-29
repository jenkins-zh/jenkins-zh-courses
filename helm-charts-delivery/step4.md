Jenkins 有丰富的[插件生态](https://plugins.jenkins.io/)，下面我们演示如何对插件进行搜索、安装、删除等操作。

首先，让我们先检查更新：`jcli plugin check`{{execute}}

然后，可以根据关键字搜索我们所需要的插件：

`jcli plugin search restful`{{execute}}

安装：`jcli plugin install pipeline-restful-api`{{execute}}

查看安装进度：`jcli center watch`{{execute}}

所有的插件安装完成后，重启后就可以看到了：`jcli restart -b`{{execute}}

等 Jenkins 重启完成后，可以看到所有安装好的插件列表：`jcli plugin list`{{execute}}

对于内网环境中的用户，也可以把插件（包括依赖）：`jcli plugin download localization-zh-cn`{{execute}}
