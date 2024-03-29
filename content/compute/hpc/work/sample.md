---
title: "作业实战"
linkTitle: "作业实战"
date: 2020-02-28T10:08:56+09:00
description: 以运行Python程序为例，介绍提交作业、查看作业结果的具体流程。
keyword: 云计算, hpc，应用场景最佳实践
draft: false
weight: 1
---

本章节以运行 Lammps 软件应用程序为例，详细介绍提交作业、查看作业结果的具体流程。

## 作业文件说明

Lammps软件应用过程中，需要用到的作业文件包括：

- 计算文件，文件格式为*in，或 .lj 。
- 其他相关文件，文件格式为.restart，*airebo，*lcbop等。

准备好文件后，跟随下面步骤提交作业。

## 操作步骤

1. 选择**产品与服务** > **计算** > **高性能计算 HPC**，进入**集群**页面。点击**提交作业**，进入提交作业页面，并设置 CPU 核心数。

   ![sample_1](../../_images/sample_1.png)

2. 选择软件及版本。

   ![sample_2](../../_images/sample_2.png)

3. 将作业文件上传至 EHPC 集群的共享目录，选择**执行命令文件**，并输入作业计算文件(如.in/.lj文件等)所在的路径，其他文件也需传输到同一目录下。

   ![sample_3](../../_images/sample_3.png)

   > **说明：**
   >
   > lammps软件，平台做了内置的作业命令，不需要用户再提交其他命令文件，这里只需要上传计算执行文件即可。与计算执行文件相关的其他文件，需要放在共享存储的同一个目录文件夹下。
   >
   > 作业文件上传步骤可参考[集群文件上传/查看/下载](/compute/hpc/work/upload)相关内容。


4. 点击**提交作业**，系统将自动分配计算任务到计算节点，进入作业状态，等待作业运行完成即可。


5. 在作业列表中，点击指定作业右侧的**查看详情**。弹出的**作业详情**窗口中，在**运行信息**一栏中可查看作业运行结果所在的存储路径。

    <img src="../../_images/sample_4.png" style="zoom:40%;" />

6. 查看作业运行结果，可参考[集群文件上传/查看/下载](/compute/hpc/work/upload)相关内容。