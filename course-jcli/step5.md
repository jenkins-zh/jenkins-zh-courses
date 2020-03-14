首先，创建一个流水线类型的任务：

`jcli job create hello-pipeline --type org.jenkinsci.plugins.workflow.job.WorkflowJob`{{execute}}

然后，添加脚本。执行下面的命令后会弹出脚本编辑框：

`jcli job edit hello-pipeline`{{execute}}

在弹出的编辑器中输入下面的流水线示例脚本：

```
pipeline {
    agent any

    stages {
        stage('hello') {
            steps {
                echo 'hello jenkins pipeline'
            }
        }
    }
}
```

执行任务 `jcli job build hello-pipeline -b`{{execute}}

查看任务执行日志 `jcli job log hello-pipeline -w`{{execute}}
