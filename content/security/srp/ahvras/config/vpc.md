---
title: "配置外网 IP 主机漏洞扫描服务"
description: 如何配置外网IP主机漏洞扫描服务
draft: false
weight: 10
keyword: 配置漏洞扫描服务, 漏洞扫描服务

---

该场景下被漏洞扫描主机建立在漏洞扫描主机所在的基础网络之外，漏洞扫描主机所在的基础网络需绑定到连通外网的EIP，且该EIP需要绑定到能够与外网连通的规则安全组。

![图](../../../_images/ras2.png) 

## 前提条件

* 已完成漏洞扫描实例部署并能点击**控制台**进入漏洞扫描实例控制台。
* 已获取漏洞扫描主机绑定的EIP地址和被扫描主机的EIP地址。

## **操作步骤**

### 漏洞扫描主机绑定EIP

1. 进入**安全资源池**页面。

2. 在左侧导航栏选择**漏洞扫描**。

   进入**扫描漏洞**页面。

3. 在目标漏洞扫描实例**操作**一栏点击**加入网络**，选择能够连接外网的EIP，点击**提交**。

4. 在目标漏洞扫描实例点击安全组ID，进入安全组详情页，放行安全组上行规则和下行规则中 TCP/UDP 协议的 1~65535 的所有端口。

   ![放行安全组规则](../../../_images/ras3.png)

5. 在目标漏洞扫描实例**操作**一栏点击**控制台**，进入漏洞扫描实例控制台首页。

6. 选择**资产列表 > 主机资产**，点击**新建**。

   ![新建](../../../_images/ras4.png)

   | 配置项   | 说明                                                         |
   | -------- | ------------------------------------------------------------ |
   | 资产名称 | 输入资产名称。                                               |
   | IP地址   | 输入要导入主机的IP地址，此处被扫描的是基础网络中的资产，应输入被扫描主机的IP地址<b>139.198.11.139</b>。 |
   | 设备类型 | 选择设备类型，此处选择<b>通用主机</b>。                      |
   | 操作系统 | 选择操作系统，此处根据选择的主机类型确认选择`Linux`。        |
   | 资产等级 | 选择资产等级。                                               |

7.  参数信息填写完成后，点击**提交**。

8. 选择**扫描任务 > 主机扫描**，点击**新建**。

   输入任务名称，扫描目标可点击**导入资产**进行选择，其他参数选择默认。 

   ![导入资产](../../../_images/ras5.png)

9. 点击，**跳过并提交**。

   > **说明**
   >
   > * 若创建任务时的**执行类型**选择的是**立即执行**，任务提交后，将会立即执行漏洞扫描任务，任务执行时间根据目标主机配置的时间而定。
   > * 若存活资产数为0的情况，说明资产不能访问，需要排查漏洞扫描中绑定的EIP、安全组是否能够通外网。

10. 待任务进度显示为100%时，点击任务名称，可查看任务执行结果详情。

    ![查看详情](../../../_images/ras6.png)