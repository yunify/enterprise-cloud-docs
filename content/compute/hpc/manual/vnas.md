---
title: "文件存储"
linkTitle: "文件存储"
description: 本章节介绍 EHPC 集群所使用的文件存储vNAS。
keyword: 云计算, EHPC，挂载集群，挂载点，文件存储，vNAS
draft: false
weight: 40
---

## 概述

EHPC 集群的存储系统采用的是文件存储 vNAS，详细内容可参考[文件存储](/storage/vnas/intro/introduction)相关内容。

## 前提条件

已创建文件存储。

## 约束限制

已经创建的挂载点仅能在创建 EHPC 集群时进行挂载。

## 使用文件存储

1. 登录管理控制平台。

2. 选择**产品与服务** > **计算** > **高性能计算 HPC**，默认进入**高性能计算 HPC** 的**集群管理**页面。


3. 点击**创建集群**。在**创建专属集群**窗口中找到**高级参数**中的**存储配置**。
  
     ![relate_cluster_3](../../_images/relate_cluster_3.png)

4. 在 **NAS 挂载点**下拉列表中，选择已创建的 vNAS 挂载点。
   
   > **说明**
   >
   > - 若无可用的挂载点可点击**创建新的 NAS 挂载点**进行创建。
   > - 创建挂载点可参考[文件存储](/storage/vnas/intro/introduction)中创建 vNAS 相关内容。

5. 挂载点选择完成后，以及其他参数配置完成后，完成集群创建即可。
