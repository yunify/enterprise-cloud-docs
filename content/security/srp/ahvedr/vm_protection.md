---
title: "资产防护配置"
description: 主机安全
draft: false
weight: 35
keyword: 云安全, 安全，主机安全

---

资产列表通过一键读取您账号下该区域内所有主机安全实例所在网络中的云服务器资产，您可将云服务器与对应主机安全实例进行关联并选择自动或手动安装 Agent，简化繁琐的 Agent 安装操作实现资产纳管目的。

本小节为您介绍如何一键安装或卸载 Agent。

## 同步资产

1. 进入**安全资源池**页面。

2. 在左侧导航栏选择**主机安全** > **资产列表**。

   进入**资产防护配置**页面。

3. 点击**同步资产**。

   可实时更新资产状态和已防护实例情况。

   ![同步资产](../../_images/vm_protection_00.png)

## 安装 Agent

1. 进入**安全资源池**页面。

2. 在左侧导航栏选择**主机安全** > **资产列表**。

   进入**资产防护配置**页面。

3. 在待卸载 Agent 的资产名称所在行操作一栏点击**安装Agent**。

   >**说明**
   >
   >若您需安装多个资产的 Agent，可勾选多个未安装 Agent 的资产并点击上方的**批量安装**。

   ![安装 Agent](../../_images/vm_protection_01.png)

4. 选择需要关联的安全实例，点击**关联实例**。

   >**注意**
   >
   >批量安装 Agent 时，也仅能选择一个安全实例进行关联。

   ![关联实例](../../_images/vm_protection_02.png)

5. 选择安装方式。

   * 自动安装：点击**一键安装**。

   * 手动安装：选择操作系统。

     >**说明**
     >
     >* Windows系统支持：Windows XP SP3 / Windows Vista / Windows 7 / Windows 8、8.1 / Windows 10 / Windows Server 2003 SP2 / Windows Server 2008、2008R2 / Windows Server 2012、2012R2 / Windows Server 2016 / Windows Server 2019
     >* Linux 系统支持：支持Centos5.0+、Redhat5.0+、Suse11+、Ubuntu 14+等主流发行版本操作系统；国产系统：中标麒麟，银河麒麟，统信UOS

     1. 复制页面上对应操作系统提供的安装命令。

        ![手动安装](../../_images/vm_protection_21.png)

     2. 登录安装客户端。

        * Windows：以管理员权限运行 CMD 程序，粘贴第一步命令进行安装。
        * Linux：以管理员权限执行第一步命令进行安装。

6. 点击**返回资产列表**查看安装进度。

   待**是否安装 Agent**一列显示`已安装`表示安装 Agent 成功。

   ![安装成功](../../_images/vm_protection_22.png)

   

## 卸载 Agent

1. 进入**安全资源池**页面。

2. 在左侧导航栏选择**主机安全** > **资产列表**。

   进入**资产防护配置**页面。

3. 在待卸载 Agent 的资产名称所在行操作一栏点击**卸载Agent**。

   弹出<b>您确定卸载Agent吗？</b>提示框。

   >**说明**
   >
   >* 卸载agent后该资产将不会被主机安全实例保护，请谨慎操作！
   >* 若您需卸载多个资产的 Agent，可勾选多个已安装 Agent 的资产并点击上方的**批量卸载**。

   ![卸载 Agent](../../_images/vm_protection_03.png)

4. 点击**确定**。

   等待卸载完成，待**是否安装 Agent**一列显示`未安装`表示卸载 Agent 成功。

   ![卸载成功](../../_images/vm_protection_04.png)

