---
title: "什么是流量牵引服务"
description: 介绍流量牵引服务、产品优势及功能。
keyword: VPC, VPC 网络, 私有网络
draft: false
weight: 10

---

**流量牵引服务**：创建网络服务实例将处于同一个二层 VLAN 网络的两端服务接入到流量牵引系统，通过 EIP 将一侧流量数据牵引到另一端网络中，使两个私有云之间网络互通。流量牵引服务提供统一的连通接口、统一的安全策略以及统一管控平台帮助用户实现多云网络（MultiCloud Networking 简称 MCN），可有效帮助用户轻松构建混合云。

流量牵引服务部署在 region 下的不同 zone 内，为用户提供接口，使不同网络平台之间的网络可以互联，让不同云厂商的网络（Vmware/Openstack/k8s/bm）能够通过 VLAN/VXLAN/BGP 模式接入 MCN 平台，通过 MCN 平台达到不同云网络之间互通的目的。此外多云网络提供了服务链的功能，可以让云厂商网络之间的流量，按服务链经过 NFV 集群模块，比如 LB/防火墙/NAT。

![intro](../../_images/mcn_intro.png)

