---
title: "产品优势"
description: QKE 产品优势
draft: false
weight: 5
keyword: 云计算, QKE, Kubernetes, 容器
---

容器引擎 QKE 相对于自建 Kubernetes 集群，在易用性、可靠性、性能、可扩展性、成本投入以及可维护性等多方面都具备独特的优势，能最大限度满足企业构建容器服务的各种需求。

## 简单易用

- 通过 WEB 界面快速创建 Kubernetes 集群，无需繁琐复杂的配置。
- 可扩展安装可视化集群管理工具，结合 QKE 控制台界面，可提供集群基础资源管理、容器应用管理两大层级的可视化能力。

## 强大集群管理

- 支持托管版及自管版两种集群形态以及不同产品组合（托管版集群 + KubeSphere、自管版集群 + <!--商用版 DevOps + -->商业版 ELK + Prometheus等），满足不同类型用户使用场景。
- 支持集群多可用区部署，保障生产环境的高稳定性和业务的高可用。
- 支持应用全生命周期的可视化管理（需安装 KubeSphere）。
- 支持多集群管理（需安装 KubeSphere）。
<!--- 支持在控制台一键完成整个集群的全面升级。-->
- 支持集群可观测性（需安装 KubeSphere）。

## 资源弹性伸缩

- 通过 QKE 控制台，轻松实现集群节点的横向及纵向扩缩容。
- 支持 Pod 横向弹性伸缩（HPA，Horizonal Pod Autoscaler）和纵向扩容（VPA，Vertical Pod Autoscaler）。
- 支持集群节点[自动弹性伸缩](../../manual/mgt_node/auto_node/)，根据资源指标数据的变化，自动完成节点的增减。
- 集成 [csi](https://github.com/yunify/qingcloud-csi) 存储插件，可以自动创建存储资源，支持硬盘自动扩容和自动迁移。

## 低成本低门槛

- 只需要按实际使用的云资源进行付费（例如云服务器、云硬盘、公网 IP、负载均衡等），无任何附加费用。
- 可选择托管版集群，节省 Master 节点费用及运维成本。
- 支持选装集群可视化工具，以 Web 界面方式管理集群及容器应用，操作简单方便。

## 稳定可靠

- 依托于云平台 IaaS 层能力，并对资源调用及管理的对接进行了优化，支持不同类型节点、支持青云块存储、支持创建负载均衡器、提供 Hostnic 网络组件实现容器网络隧道直通能够为集群提供更好的稳定性。
- 支持 3 Master HA 高可用，集群节点和工作负载支持跨可用区（AZ）部署，帮助您轻松构建同城多活业务架构，保障您的业务高可用，获得生产环境的高稳定性。

## 安全高效

- 支持私有网络部署集群，网络完全隔离、自主掌控，您可以使用您自己的安全组和网络 ACL，构建高度安全可靠的应用程序。

- 支持持续集成/持续交付 (CI/CD)。可构建独立 DevOps 工程、支持 Binary-to-Image（B2I）、Source-to-Image（S2I）快速制作镜像，提供代码依赖缓存支持，以及代码质量管理与流水线日志等功能，快速构建、升级、回滚应用环境。


## 开放灵活

QKE 遵循青云开源、自由的理念，旨在为用户提供自由的、不受绑定的云原生服务，可对接多种开源在线服务及产品、周边系统、开发运维工具，可管理不同环境、多个厂商的 Kubernetes 集群。


