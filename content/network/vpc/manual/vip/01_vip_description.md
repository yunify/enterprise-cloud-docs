---
title: "内网 VIP 概述"
keyword: VPC, 云服务器, 虚拟IP,VIP
description: 什么是内网 VIP
draft: false
weight: 1
---

## 什么是内网 VIP

内网 VIP 包括 **VBC 网络 IP** 和 **VPC 网络 IP**。

- VBC 网络 IP 是从基础网络子网 CIDR 分配的一个内网 IP 地址，是云平台租户公有的 IP 地址，租户可以预先占用、查看和释放地址。
- VPC 网络 IP 是从 VPC 网络子网 CIDR 分配的一个内网 IP 地址，是云平台租户私有的 IP 地址，由租户自己管理，租户可分配、查看和释放地址。

每个 VBC/VPC 下可以申请多个内网 VIP 地址。一般由网络管理员预先申请并分配 IP 地址，使用者需要使用时再进行绑定或配置。内网 VIP 可以与负载均衡器或云服务器进行绑定，并可搭配高可用软件（例如 Keepalived）使用，搭建高可用主备服务，提高业务的可用性。

## 使用场景

- 部署高可用服务

  例如，您需要避免单点故障，提高服务的高可用性，可以用“一主一备”或“一主多备”的方法组合使用云服务器，这些云服务器用内网 VIP 作为统一对外的 IP。当主服务器故障时，备服务器可以转为主服务器，继续对外提供服务。

  ![](../../../_images/vip.svg)

- 部署高可用负载均衡集群

  例如，部署负载均衡集群时，在负载均衡之间做 HA，后端机器做集群。因此部署负载均衡的两台服务器间要部署 HA，用内网 VIP 作为统一对外的 IP。


## 限制说明

- 内网 VIP 具有子网属性，只能绑定到同一子网下的资源。
- 内网 VIP 与云服务器绑定时，不支持手动在控制台将内网 VIP 绑定指定云服务器，需要在云服务器上进行配置。
