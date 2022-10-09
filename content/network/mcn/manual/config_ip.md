---
title: "配置路由到回源 IP"
description: 介绍流量牵引服务、产品优势及功能。
keyword: 回源IP, 流量牵引服务
draft: false
weight: 30


---

本小节介绍如何在互联网实例侧配置路由到回源 IP。

## 前提条件

* 已获取安全实例云服务器 IP 地址。

* 待配置网络与互联实例需在同一 VLAN 二层网络中。

  >**说明**
  >
  >本小节以 Linux 模拟第三方安全实例为例，具体配置参数以实际环境为准。

## 操作步骤

1. 登录待配置流量牵引服务的云服务器。

2. 执行以下命令创建网络命令空间。

   ```
   ip netns add <网络空间名称>
   ```

   例如

   ```
   ip netns add ns_vm_218_10
   ```

3. 执行以下命令查看网络空间是否创建成功。

   ```
   ip netns |grep <网络空间名>
   ```

   例如

   ```
   ip netns |grep 218
   ```

4. 执行以下命令列出节点上的网卡信息。

   ```
   ip link list
   ```

5. 执行以下命令创建虚拟网卡。

   ```
   ip link add <虚拟网卡名称1> type veth peer name <虚拟网卡名称>
   ```

6. 执行以下命令将新建的虚拟网卡添加至新建的网络命名空间。

   ```
   ip link set <虚拟网卡名称> netns <网络空间名称>
   ```

   例如

   ```
   ip link set test1 netns ns_vm_218_10
   ```

7. 执行以下命令验证网卡添加效果。

   ```bash
   ip netns exec <网络空间名称> ip link list
   ```

   例如

   ```bash
   ip netns exec ns_vm_218_10 ip link list
   ```

   ![验证](../../_images/config_mcn_ip02.png)

8. 执行以下命令添加实例 IP

   ```bash
   ip netns exec <网络空间名称> ip addr add <实例 IP> dev <虚拟网卡名称>
   ip netns exec <网络空间名称> ip link set <虚拟网卡名称> up
   ip netns exec <网络空间名称> ip link set lo up
   ```

   例如

   ```bash
   ip netns exec ns_vm_218_10 ip addr add 10.50.20.1/24 dev vm_218_10
   ip netns exec ns_vm_218_10 ip link set vm_218_10 up
   ip netns exec ns_vm_218_10 ip link set lo up
   ```

   

9. 执行以下命令检查实例 IP 是否配置成功。

   若能 ping 通这表示实例 IP 配置成功。

   ```bash
   ip netns exec <网络空间名称> ping <实例 IP>
   ```

   例如

   ```bash
   ip netns exec ns_vm_218_10 ping 10.50.20.1
   ```

   

10. 执行以下命令回源 IP。

    ```bash
    ip netns exec <网络空间名称> route add -host <EIP 地址> gw <回源 IP 地址>
    ```

    例如

    ```bash
    ip netns exec ns_vm_218_10 route add -host 192.168.8.173 gw 10.50.20.2
    ```

11. 执行以下命令查询是否回源成功。

    ```
    ip netns exec <网络空间名称> route -n
    ```

    例如

    ```bash
    ip netns exec ns_vm_218_10 route -n
    ```

    显示以下信息表示配置回源 IP 地址成功。

    <img src="../../_images/config_mcn_ip03.png" style="zoom: 100;" />

