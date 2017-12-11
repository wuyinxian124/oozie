oozie 基本概念   


任务：计算或者执行任务。
Action: An execution/computation task (Map-Reduce job, Pig job, a shell command). It can also be referred as task or 'action node'.

工作流：一系列任务组成的有向无环图。任务之间有依赖关系，只有前一个任务执行完，才会触发下一个任务执行。      
Workflow: A collection of actions arranged in a control dependency DAG (Direct Acyclic Graph). "control dependency" from one action to another means that the second action can't run until the first action has completed.

工作流的定义：  
Workflow Definition: A programmatic description of a workflow that can be executed.

工作流编写语言：  
Workflow Definition Language: The language used to define a Workflow Definition.

job:  
Workflow Job: An executable instance of a workflow definition.

engine:    
Workflow Engine: A system that executes workflows jobs. It can also be referred as a DAG engine.
