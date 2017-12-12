# oozie 介绍

oozie 是一个用来运行mr和pig 任务的工作流引擎。  

oozie 包括任务节点和控制节点。运行节点是包括mr 和pig 等任务。控制节点控制任务的流向。整个工作流是由控制节点和运行节点组成的一个有向无环图。

工作流的编写语言是phdl,格式是xml。

Oozie workflows definitions are written in hPDL (a XML Process Definition Language similar to JBOSS JBPM jPDL).

运行任务实际是在远端，如yarn或者hadoop，当提交的任务完成，远端就会回调oozie 接口，oozie 知道这个任务完成就会提交下一个任务。
Oozie workflow actions start jobs in remote systems (i.e. Hadoop, Pig). Upon action completion, the remote systems callback Oozie to notify the action completion, at this point Oozie proceeds to the next action in the workflow.

工作流的任务有两种类型：控制节点和计算任务。


控制节点定义了工作流的开始和结束（有开始节点，结束节点，失败节点），也提供了控制任务链的执行路径的方式（ decision , fork and join）。

计算节点提供计算任务和处理任务。oozie 现在提供了多种任务类型：mr,pig，http等。oozie 也支持添加自定义任务类型。
Action nodes are the mechanism by which a workflow triggers the execution of a computation/processing task. Oozie provides support for different types of actions: Hadoop map-reduce, Hadoop file system, Pig, SSH, HTTP, eMail and Oozie sub-workflow. Oozie can be extended to support additional type of actions.

oozie 提供参数化的功能，通过在工作流中设置参数，在任务参数中使用工作流的参，类似${inputDir}   
 
Oozie workflows can be parameterized (using variables like ${inputDir} within the workflow definition). When submitting a workflow job values for the parameters must be provided. If properly parameterized (i.e. using different output directories) several identical workflow jobs can concurrently.
