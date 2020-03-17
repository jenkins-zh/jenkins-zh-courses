#### 创建 Job

点击`新建任务`或`创建一个新任务`，
输入任务名称（如：maven-pipeline-demo），
类型选择`流水线`，然后点击`确定`按钮。

任务配置中，`流水线`区域`定义`下拉框，选择 `Pipeline script`，
脚本区域右上角的 `try Sample Pipeline` 下拉框选择 `GitHub + Maven`，
可以看到脚本区域就被如下 Pipeline 填充：

```
pipeline {
   agent any

   tools {
      // Install the Maven version configured as "M3" and add it to the path.
      maven "M3"
   }

   stages {
      stage('Build') {
         steps {
            // Get some code from a GitHub repository
            git 'https://github.com/jglick/simple-maven-project-with-tests.git'

            // Run Maven on a Unix agent.
            sh "mvn -Dmaven.test.failure.ignore=true clean package"

            // To run Maven on a Windows agent, use
            // bat "mvn -Dmaven.test.failure.ignore=true clean package"
         }

         post {
            // If Maven was able to run the tests, even if some of the test
            // failed, record the test results and archive the jar file.
            success {
               junit '**/target/surefire-reports/TEST-*.xml'
               archiveArtifacts 'target/*.jar'
            }
         }
      }
   }
}
```

该 Pipeline 下的 `stages` 包括一个 `stage('Build')`，这个 `stage` 的 `steps` 中会从 github 下载代码，然后使用 maven 构建项目，
如果构建成功的话，会运行 `post` 区域的指令，包括发布 junit 报告以及存档 artifact。

其中，Maven 已事先在`系统管理-->全局工具配置`中配置好。

点击 `保存` 按钮，Job 就创建成功了。
