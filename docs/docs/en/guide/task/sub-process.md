# SubProcess Node

## Overview

The sub-process node is to execute an external workflow definition as a task node.

## Create Task

-  Click `Project Management -> Project Name -> Workflow Definition`, and click the `Create Workflow` button to enter the DAG editing page.
- Drag from the toolbar <img src="../../../../img/tasks/icons/sub_process.png" width="15"/> task node to canvas to create a new SubProcess task.

## Task Parameter

| **Parameter** | **Description** |
| ---- |---------|
| Node name | Unique name of node in workflow definition. |
| Run flag | Identifies whether this node schedules normally. |
| Description | Describe the function of the node. |
| Task priority | When the number of worker threads is insufficient, execute in the order of priority from high to low, and tasks with the same priority will execute in a first-in first-out order. |
| Worker group | Assign tasks to the machines of the worker group to execute. If `Default` is selected, randomly select a worker machine for execution. |
| Task group name | The group in Resources, if not configured, it will not be used. |
| Environment Name | Configure the environment name in which run the script. |
| Timeout alarm | Check the timeout alarm and timeout failure. When the task runs exceed the "timeout", an alarm email will send and the task execution will fail. |
| Child node | It is the workflow definition of the selected sub-process. Enter the child node in the upper right corner to jump to the workflow definition of the selected sub-process. |
| Pre task | Selecting a predecessor task for the current task, will set the selected predecessor task as upstream of the current task.

## Task Example

This example simulates a common task type, here we use a child node task to recall the [Shell](shell.md) to print out "hello". This means executing a shell task as a child node.

### Create a Shell task

Create a shell task to print "hello" and define the workflow as `test_dag01`.

![subprocess_task01](../../../../img/tasks/demo/subprocess_task01.png)

## Create the Sub_process task

To use the sub_process, you need to create the sub-node task, which is the shell task we created in the first step. After that, as shown in the diagram below, select the corresponding sub-node in position ⑤.

![subprocess_task02](../../../../img/tasks/demo/subprocess_task02.png)

After creating the sub_process, create a corresponding shell task for printing "world" and link both together. Save the current workflow and run it to get the expected result.

![subprocess_task03](../../../../img/tasks/demo/subprocess_task03.png)

## Note

When using `sub_process` to recall a sub-node task, you need to ensure that the defined sub-node is online status, otherwise, the sub_process workflow will not work properly.
