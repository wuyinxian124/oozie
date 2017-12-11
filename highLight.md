oozie 重要事项  

一个工作流应用包括以下任务类型：hadoop,pig和子工作流。  
A Workflow application is DAG that coordinates the following types of actions: Hadoop, Pig, and sub-workflows.

在工作流中起控制作用的是 fork,join,decision等节点。工作流不支持周期性执行。  
Flow control operations within the workflow applications can be done using decision, fork and join nodes. Cycles in workflows are not supported.

Actions and decisions can be parameterized with job properties, actions output (i.e. Hadoop counters) and file information (file exists, file size, etc). Formal parameters are expressed in the workflow definition as ${VAR} variables.

一个工作流应最终形成一个zip ,其中包括工作流定义的xml 文件，以及所有其他依赖资源，包括mr任务jar包，shell 脚本，依赖libs,pig 脚本等内容。  
A Workflow application is a ZIP file that contains the workflow definition (an XML file), all the necessary files to run all the actions: JAR files for Map/Reduce jobs, shells for streaming Map/Reduce jobs, native libraries, Pig scripts, and other resource files.

在运行一个工作流之前，这个工作流必须已经部署到oozie中。  
Before running a workflow job, the corresponding workflow application must be deployed in Oozie.

部署或运行一个工作流，可以通过命令行，java api 等方式。
Deploying workflow application and running workflow jobs can be done via command line tools, a WS API and a Java API.

监控系统或工作流，可以通过命令行或者java api 等方式。  
Monitoring the system and workflow jobs can be done via a web console, command line tools, a WS API and a Java API.

当提交工作流，在工作流中定义的属性对应的参数都将被格式化。  
When submitting a workflow job, a set of properties resolving all the formal parameters in the workflow definitions must be provided. This set of properties is a Hadoop configuration.

工作流中的任务状态包括：prep,running,suspended,SUCCEEDED,killed,failed.  
Possible states for a workflow jobs are: PREP , RUNNING , SUSPENDED , SUCCEEDED , KILLED and FAILED .

万一工作流中节点启动失败，oozie 将根据失败类型，决定是自动重跑，还是提醒手动重跑，或者是将整个工作流失败。  
In the case of a action start failure in a workflow job, depending on the type of failure, Oozie will attempt automatic retries, it will request a manual retry or it will fail the workflow job.

任务如下状态 出现的时候（start,end,failure），oozie 可以通过http回调触发工作流的终止和失败事件。  
Oozie can make HTTP callback notifications on action start/end/failure events and workflow end/failure events.

如果有任务失败，重新提交工作流，会跳过之前成功过的任务。在重新提交工作流之前，可以给工作流资源打一个补丁，修复工作流中存在的代码问题。  
In the case of workflow job failure, the workflow job can be resubmitted skipping previously completed actions. Before doing a resubmission the workflow application could be updated with a patch to fix a problem in the workflow application code.
