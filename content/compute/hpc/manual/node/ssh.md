---
title: "WebSSH登录"
linkTitle: "WebSSH登录"
date: 2021-11-1T10:08:56+09:00
description: hpc WebSSH登录
keyword: 云计算, HPC，WebSSH登录
draft: false
weight: 50
---

本章节介绍如何配置 EHPC 集群登录节点的 WebSSH 登录。

## 前提条件

- 已创建 EHPC 集群。

- 仅登录节点支持 WebSSH 登录。

## 操作步骤

### webSSH 远程连接

1. 登录管理控制平台。

2. 选择**产品与服务** > **计算** > **高性能计算 HPC**，默认进入**集群**页面。


3. 点击已创建完成的集群 ID，进入集群详情页面，选择**节点列表**页签。 在**节点列表**页面，点击待重启节点所在行的<img src="../../../_images/more_operation.png" style="zoom:50%;" />，选择 **WebSSH**。

   ![ssh_1](../../../_images/ssh_1.png)

3. 在弹出的**远程连接**窗口中，选择 **WebSSH 远程连接**，并输入用户名和密码，点击**确定**即可。
   > **说明**：
   >
   > 用户名和密码为集群内已存在的户名和密码，可通过进入集群详情页面内的用户列表进行查看。
   
   <img src="../../../_images/remote_login_2.png" style="zoom:50%;" />




