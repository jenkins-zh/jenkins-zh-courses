首先，创建一个流水线类型的任务：

`jcli job create go-pipeline --type org.jenkinsci.plugins.workflow.job.WorkflowJob`{{execute}}

然后，添加脚本。执行下面的命令后会弹出脚本编辑框：

`jcli job edit go-pipeline`{{execute}}

在弹出的编辑器中输入下面的流水线示例脚本(完成简单Go 工程的创建、构建和执行生成的可执行文件)：

```
pipeline {
    agent any

    stages {
        stage('create a simple go project') {
            steps {
                sh label: '', script: '''cat <<_EOF>hello.go
package main
import "fmt"
func main() {
    fmt.Println("Hello, World!")
}
_EOF'''
            }
        }
        stage('go build') {
            steps {
                sh label: '', script: 'go build hello.go'
            }
        }
        stage('run the executable file created by go build') {
            steps {
                sh label: '', script: './hello'
            }
        }
        
    }
}
```

执行任务 `jcli job build go-pipeline -b`{{execute}}

查看任务执行日志 `jcli job log go-pipeline -w`{{execute}}
