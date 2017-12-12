
## 工作流  

工作流节点包括控制节点和任务节点。  
Workflow nodes are classified in control flow nodes and action nodes:

控制节点标示工作流的起始，终止或者是控制工作流执行路径。    
Control flow nodes: nodes that control the start and end of the workflow and workflow job execution path.

行为节点 主要任务是计算和执行任务。  
Action nodes: nodes that trigger the execution of a computation/processing task.

节点格式必须满足 ```[a-zA-Z][\-_a-zA-Z0-0]*=```,长度不能超过20个字节。  
Node names and transitions must be conform to the following pattern =[a-zA-Z][\-_a-zA-Z0-0]*=, of up to 20 characters long.
