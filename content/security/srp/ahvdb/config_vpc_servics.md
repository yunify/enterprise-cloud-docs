---
title: "配置数据库审计服务"
description: 购买数据库审计
draft: false
weight: 40
keyword: 云安全, 安全，数据库审计

---

数据库审计服务需在数据库审计实例控制台进行资产和规则配置才可正常使用。且数据库审计实例与被审计主机需处于同一网络中，若被审计主机与数据库审计实例主机不在同一网络，两者需绑定到同一VPC网络中。本章节以绑定到VPC网络中的场景为例。

该场景下数据库审计主机（VM）创建时加入到基础网络，数据库审计实例部署后需绑定到VPC，实现数据库审计主机和VPC内的待防护主机通信且对VPC内的主机进行数据库审计。

![图](../../_images/dbs1.png) 

## 前提条件

* 已完成数据库审计实例部署并能点击**控制台**进入数据库审计实例控制台。
* 已获取数据库审计主机IP地址、VPC网络地址和VPC网络中数据库防护主机 IP地址。

## 操作步骤

### 加入网段

1. 进入**安全资源池**页面。

2. 在左侧导航栏选择**数据库审计**。

   进入**数据库审计**页面。

3. 在目标日志审计实例**操作**一栏点击**加入网络**，选择数据库审计防护主机所在的VPC和私有网络，点击**提交**。

   VPC网络添加成功后，可在实例**网络**一栏查看VPC网络地址。

### 添加资产

4. 在目标日志审计实例**操作**一栏点击**控制台**，进入数据库审计实例控制台首页。

5. 选择**资产 > 资产管理**，点击**添加**。

6. 输入参数。

   IP地址输入VPC 中数据库审计防护的服务器名称。

   ![输入参数](../../_images/dbs2.png) 

### 安装 Agent

7. 选择**系统管理 > Agent 管理 > Agent 安装**，点击**开始安装**。

   ![安装Agent](../../_images/dbs3.png) 

8. 填写审计服务器IP 、数据库服务器IP地址和root密码。

   > **说明**
   >
   > * 本操作以审计服务器IP的**172.17.0.5**和数据库服务器IP的**172.17.0.2**为例。
   > * 计服务器IP请填写与保护数据库的所在同一网段地址，如果填写与安恒资源池通信的网络地址agent运行状态为异常。

   ![输入审计IP](../../_images/dbs4.png) 

9.  点击**安装**。

   安装成功后，可点击**安装状态**查看安装详情。

10. 选择**规则配置 > 安全规则 > 规则管理**，点击名称前的勾选框全选规则，点击**启用选中项**，启动所有规则应用到保护资产。

    ![启用规则](../../_images/dbs5.png) 

### 验证数据库审计服务

11. 选择**查询分析 > 审计日志**，进入**审计日志**页面可查看操作数据。

12. 选择**规则配置 > 安全规则**，点击**新增**。

13. 在**客户端**页签**客户端来源**选择**IP**，并输入IP地址**192.168.7.100**，添加对**192.168.7.100**链接的告警， 使用**192.168.7.100**主机链接数据库。其他参数选择默认。点击**保存**。

    ![配置告警](../../_images/dbs6.png) 

14. 选择**查询分析 > 告警日志**，查看告警日志存在**192.168.7.100**链接的告警，则验证成功。

    ![验证告警](../../_images/dbs8.png)
