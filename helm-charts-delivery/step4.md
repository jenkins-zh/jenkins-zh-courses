首先，通过下面的命令或者手动创建一个流水线类型的任务：

`jcli job create hello-pipeline --type org.jenkinsci.plugins.workflow.job.WorkflowJob`{{execute}}

然后，利用命令添加脚本：

`jcli job edit hello-pipeline --url https://raw.githubusercontent.com/devops-ws/learn-pipeline-go/master/Jenkinsfile`{{execute}}

或者，手动添加流水线脚本`https://raw.githubusercontent.com/devops-ws/learn-pipeline-go/master/Jenkinsfile`{{open}}

执行任务 `jcli job build hello-pipeline -b`{{execute}}

查看任务执行日志 `jcli job log hello-pipeline -w`{{execute}}
