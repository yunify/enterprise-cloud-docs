---
title: "基础操作"
linkTitle: "基础操作"
description: 创建集群和创建挂载点
keyword: 云计算,HPC，创建集群
draft: false
weight: 10
---

本章节介绍如何创建集群。

## 前提条件

- 已获取管理控制台账号和密码。

- 已完成个人实名认证且账户余额大于 0 元。

- 已开通弹性高性能计算 HPC 服务。



## 创建 EHPC 集群

详细内容可参考[创建 EHPC 集群](/compute/hpc/quick-start/create_ehpc)


## 创建挂载点

1. 登录管理控制平台，创建 EHPC 集群，在**高级参数**配置页面，点击**创建新的 NAS 挂载点**，跳转至**文件存储 vNAS**页面。

   ![base_1](../../_images/base_1.png)

2. 在文件系统页面，点击**创建**，在弹出的**创建 NAS**窗口中，配置各项参数，点击**确认**即可。
   > **说明**
   >
   > - 创建 NAS 时，配置建议选择中型或大型.
   > - 需要选择 EHPC 集群所在的 **VPC 网络**。
   > - 需要选择 EHPC 集群所在的**私有网络**。

   <img src="../../_images/base_2.png" style="zoom:40%;" />


3. 点击已创建成功的文件系统的 ID，进入其详情页面，在**共享存储目标**页签内，点击**创建**。

   ![base_3](../../_images/base_3.png)

4. 在弹出的**创建共享存储目标**窗口中，选择目标类型为 NFS，配置各项参数后点击**提交**。

   <img src="../../_images/base_4.png" style="zoom:40%;" />

   参数说明：

    <table>
    <tr>
     <th style="width:30%">参数</th>
     <th style="width:70%">说明</th>
    </tr>
    <tr>
     <td>目标类型</td>
     <td> 选择 NFS 类型</td>
    </tr>
    <tr>
     <td>共享目录</td>
     <td>用户自定义目录名称</td>
    </tr>
    <tr>
     <td>硬盘</td>
     <td>建议使用新申请的容量型或性能型硬盘</td>
    </tr>
    <tr>
     <td>权限组</td>
     <td>若平台内已经存在权限组，点击<b>选择权限组</b>，若无权限组，则需点击<b>创建权限组</b>进行创建</td>
    </tr>
    </table>

5. 返回共享存储目标页签，点击**应用修改**，使得创建的共享存储目录生效即可。

    ![base_5](../../_images/base_5.png)

6. 关于文件存储 vNAS的更多操作，详细内容可参考[文件存储](/storage/vnas/intro/introduction)相关内容。

