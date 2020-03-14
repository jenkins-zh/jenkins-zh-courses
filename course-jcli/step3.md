在用户根目录下，增加 jcli 的配置文件：

`jcli config gen -i=false > ~/.jenkins-cli.yaml`{{execute}}

然后，利用命令 `sed -i "s%token:.*%token: admin%g" ~/.jenkins-cli.yaml`{{execute}} 把配置文件中的 `token` 修改为 `admin`：

```
current: yourServer
language: ""
jenkins_servers:
- name: yourServer
  url: http://localhost:8080/jenkins
  username: admin
  token: admin
  proxy: ""
  proxyAuth: ""
  insecureSkipVerify: true
  description: ""
preHooks: []
postHooks: []
pluginSuites: []
mirrors:
- name: default
  url: http://mirrors.jenkins.io/
- name: tsinghua
  url: https://mirrors.tuna.tsinghua.edu.cn/jenkins/
- name: huawei
  url: https://mirrors.huaweicloud.com/jenkins/
- name: tencent
  url: https://mirrors.cloud.tencent.com/jenkins/
```

如果您仔细观察的话，可以发现，上面的配置文件中可以配置多个 Jenkins。下面的命令可以让你看到当前所选择的地址信息：

`jcli config`{{execute}}
