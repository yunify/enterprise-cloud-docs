---
title: "为云服务器配置内网 VIP"
keyword: VPC,虚拟 IP,VBC,内网VIP
description: 介绍如何将内网 VIP 应用于到云服务器。
draft: false
weight: 30
---

本文介绍如何将申请的内网 VIP 绑定到云服务器上。

## 前提条件

已申请内网 VIP。

## 注意事项

一个 VIP 只能绑定在一台云服务器上，否则可能会引发  ARP 信息的不一致。

## 在 CentOS 系统上配置

以下方法以 CentOS7 系统为例。

**固化配置**：

1. 复制一份 ifcfg-eth0 配置文件，命名为 “ifcfg-eth0:0”。

   ```
   cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0:0
   ```

2. 修改 ifcfg-eth0:1 配置文件。

   ```
   vim /etc/sysconfig/network-scripts/ifcfg-eth0:0
   ```

   按 **i** 进入编辑模式，修改配置：

   - 将 “IPADDR=” 后面的 IP 改为您申请到的内网 VIP
   - 将 DEVICE="eth0" 改为 DEVICE="eth0:0"
   - 删除 "GATEWAY=" 这一行

   修改后，保存并退出文件。

3. 重启网络。

   ```
   service network restart
   ```

4. 检查 VIP 是否添加成功。

   ```
   ip a
   ```

5. 使用 **arping** 命令通告 arp 信息。

   假设您申请的内网 VIP 为 10.10.1.x，执行如下命令。

   ```
   arping -U 10.10.1.x
   ```

**临时配置**：

>**说明**
>
>该方法临时生效，服务器重启或网络重启将失效，需要重新添加。

1. 添加内网 VIP。

   假设您申请的内网 VIP 为 10.10.1.x，执行如下命令。

   ```
   ip addr add 10.10.1.x/24 dev eth0
   ```

2. 检查 VIP 是否添加成功。

   ```
   ip a
   ```

3. 使用 **arping** 命令通告 arp 信息。

   ```
   arping -U 10.10.1.x
   ```

## 在 Ubuntu 系统上配置

**固化配置**：

1. 修改网络配置文件。

   ```
   sudo vim /etc/network/interfaces
   ```

   按 **i** 进入编辑模式，将配置文件里的内容复制一份，然后修改复制的内容：

   - “eth0” 替换为 “eth0:0”
   - 在 “address” 后填入申请到的内网 VIP

   修改后的配置文件示例如下：

   ```
   # The primary network interface
   auto eth0
   iface eth0 inet static
   address 10.10.1.23
   netmask 255.255.255.0
   gateway 10.10.1.1
   dns-nameservers 10.255.255.1
   
   auto eth0:0
   iface eth0:0 inet static
   address 10.10.1.x   #此处填入申请的内网 VIP
   netmask 255.255.0.0
   gateway 10.4.0.1
   dns-nameservers 10.255.255.1
   ```

   修改后，保存并退出文件。

2. 重启网络服务。

   ```
    sudo /etc/init.d/networking restart
   ```

3. 检查 VIP 是否添加成功。

   ```
   ip a
   ```

4. 使用 **arping** 命令通告 arp 信息。

   假设您申请的内网 VIP 为 10.10.1.x，执行如下命令。

   ```
   arping -U 10.10.1.x
   ```

**临时配置**：

>**说明**
>
>该方法临时生效，服务器重启或网络重启将失效，需要重新添加。

1. 添加内网 VIP。

   假设您申请的内网 VIP 为 10.10.1.x，执行如下命令。

   ```
   ip addr add 10.10.1.x/24 dev eth0:0
   ```

2. 检查 VIP 是否添加成功。

   ```
   ip a
   ```

3. 使用 **arping** 命令通告 arp 信息。

   ```
   arping -U 10.10.1.x
   ```

