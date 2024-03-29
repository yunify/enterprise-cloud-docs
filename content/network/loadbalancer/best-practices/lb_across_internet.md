---
title: "使用负载均衡器实现跨公网的高可用网络服务"
description: 介绍如何使用负载均衡器实现跨公网的高可用网络服务。
keyword: 负载均衡器, 跨公网
draft: false
---

本节描述了如何灵活运用VPC、NAT网关、路由表、负载均衡器，搭建跨公网的负载均衡架构，从而实现多地域的高可用网络服务。

## 借助 NAT 网关的 SNAT 功能

NAT 网关为私有网络的云服务器提供了复用公网 IP 的能力，云服务器可以共用 NAT 网关绑定的公网 IP 地址访问互联网。

### 步骤1：创建 VPC 网络

1. 在菜单栏，选择**产品与服务** > **网络服务** > **VPC 网络**，进入**VPC 网络**页面。

2. 点击**创建 VPC 网络**，创建一个 VPC 网络及初始私有网络。

   初始私有网络关联默认路由表。操作详情参见[创建 VPC 网络](/network/vpc/manual/vpcnet/10_create_vpc/)。

   ![](../_images/lb+natgw1.png)

### 步骤2：创建 NAT 网关及 SNAT 规则

1. 在菜单栏，选择**产品与服务** > **网络服务** > **NAT 网关**，进入**NAT 网关**页面。

2. 点击**创建**，创建一个 NAT 网关。

   创建 NAT 网关时，VPC 网络选择[步骤1](#步骤1创建-vpc-网络)所创建的 VPC 网络，公网 IP选择**购买并绑定**。

   ![](../_images/lb+natgw2.png)

3. 创建完成后点击 NAT 网关 ID，进入详情页。

4. 点击**添加规则**，添加 SNAT 规则。

   **资源类型**选择私有网络，然后选择[步骤1](#步骤1创建-vpc-网络)中所创建的初始私有网络。

   ![](../_images/lb+natgw3.png)

5. 添加完成后，点击**应用修改**。

   至此，私有网络内的云服务器便可以通过 NAT 网关访问互联网。

### 步骤3：创建负载均衡器并添加公网后端

1. 在菜单栏，选择**产品与服务** > **网络服务** > **负载均衡器**，进入**负载均衡器**页面。

2. 点击**创建**，创建一个负载均衡器。

   为负载均衡器绑定公网 IP（需提前创建），并绑定[步骤1](#步骤1创建-vpc-网络)中所创建的初始私有网络。

   ![](../_images/lb+natgw4.png)

3. 创建完成后，点击负载均衡器 ID，进入详情页。

4. 点击**创建监听器**，创建一个 HTTP 协议监听器，然后点击**应用修改**。

   ![](../_images/lb+natgw5.png)

5. 点击**添加后端**，此时便可直接通过 IP 添加一个跨区域的后端。

   填写后端服务器的公网 IP 及服务端口。

   ![](../_images/lb+natgw6.png)

### 步骤4：配置安全组规则

通过配置安全组规则，放行 NAT 网关及负载均衡器的下行流量。

1. 在菜单栏，选择**产品与服务** > **安全服务** > **安全组**，进入**安全组**页面。

2. 找到 NAT 网关及负载均衡器所绑定的安全组，点击安全组 ID，进入安全组规则配置页面。

3. 点击**添加规则**，配置规则，点击**提交**。

   ![](../_images/lb+natgw10.png)

4. 点击**应用修改**。

5. 去负载均衡器的监听器页面，观察所添加的后端的状态变为`活跃`，表示后端已经可用了。

   ![](../_images/lb+natgw12.png)

## 借助 VPC 的 SNAT 能力

VPC自带 SNAT 功能，VPC 内部的网络可以借助 VPC 绑定的公网 IP 访问到公网。负载均衡可借助 VPC 的 SNAT 功能，将公网 IP 作为后端。

网络架构如图所示：

![](../_images/lb+vpc1.png)

### 步骤1：创建 VPC 网络并绑定公网 IP

1. 在菜单栏，选择**产品与服务** > **网络服务** > **VPC 网络**，进入**VPC 网络**页面。

2. 点击**创建 VPC 网络**，创建一个 VPC 网络。

   创建时，**类型**需选择非免费型，**公网 IP** 选择**购买并绑定**，为 VPC 网络绑定公网 IP。操作详情参见[创建 VPC 网络](/network/vpc/manual/vpcnet/10_create_vpc/)。

   ![](../_images/lb+vpc2.png)

### 步骤2：创建负载均衡器并添加公网后端

1. 在菜单栏，选择**产品与服务** > **网络服务** > **负载均衡器**，进入**负载均衡器**页面。

2. 点击**创建**，创建一个负载均衡器。

   为负载均衡器绑定公网 IP（需提前创建）及[步骤1](#步骤1创建-vpc-网络并绑定公网-ip)中所创建的私有网络。

   ![](../_images/lb+natgw4.png)

3. 创建完成后，点击负载均衡器 ID，进入详情页。

4. 点击**创建监听器**，创建一个 HTTP 协议监听器，然后点击**应用修改**。

   ![](../_images/lb+natgw5.png)

5. 点击**添加后端**，此时便可直接通过公网 IP 添加一个跨地域的后端。

   填写后端服务器的公网 IP 及服务端口。

   ![](../_images/lb+natgw6.png)

### 步骤3：添加路由规则指向路由器

1. 找到负载均衡器所属私有网络关联的路由表，点击路由表 ID，进入路由规则配置页面。

2. 点击**添加路由**，配置路由规则。

   目标网络填写公网后端 IP 地址，下一跳选择**路由器**，并选择[步骤1](#步骤1创建-vpc-网络并绑定公网-ip)中所创建的 VPC 网络。

   ![](../_images/lb+vpc3.png)

