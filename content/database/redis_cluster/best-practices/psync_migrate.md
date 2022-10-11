---
title: "使用 RedisShake 实现 Redis 跨集群异步复制"
description: 介绍如何使用 RedisShake 实现 Redis 跨集群异步复制
weight: 10
collapsible: false
draft: false
keyword:  Redis Cluster，数据库，RedisShake

---

## 场景描述

Redis Cluster 和 Redis Standalone 可通过 RedisShake 进行同集群或跨集群的数据异步复制，实现灾备和多活的业务场景，同时也免去双写的业务开销。RedisShake 的基本原理则是模拟一个从节点加入源 Redis 集群进行全量拉取并回放，然后进行增量的拉取（通过psync命令）实现目的集群与源集群的异步复制。

## 约束与限制

* 源集群支持以下版本：
  - Redis Cluster 6.x
  - Redis Cluster 5.x
  - Redis Standalone 6.x
  - Redis Standalone 5.x

* 目的集群支持以下版本：
  - Redis Cluster 6.x
  - Redis Cluster 5.x
  - Redis Standalone 6.x
  - Redis Standalone 5.x

## 前提条件

* 已创建源集群和目的集群。
* 已获取源集群和目的集群的类型和 IP 地址。

## 操作步骤

进入 RedisShake 集群创建界面。

### 第1步：基本设置

1. 在顶部**区域**下拉框中，选择部署区域。

2. 填写 RedisShake 集群的基本信息，包括：名称、描述、选择版本、计费方式、自动备份时间和可用区。

   ![基本设置](../../_images/redisshake_01.png)

### 第2步：节点设置

选择主机类型、CPU和内存规格。主机类型推荐选择`企业型 e3`，实际请根据集群情况选择规格。

![节点设置](../../_images/redisshake_02.png)

### 第3步：网络设置

选择 VPC 网络、私有网络以及节点 IP 类型。

>VPC 网络和私有网络需选择能够同时访问到源集群与目标集群的网络。

![网络设置](../../_images/redisshake_03.png)

### 第4步：服务环境参数设置

1. 填写必填参数。

   ![网络设置](../../_images/redisshake_04.png)

   * **source.type**：选择源集群 Redis 的类型。这里的 `standalone` 表示 Redis Standalone 集群，`集群`表示 Redis Cluster 集群。
   * **source.address**：输入源 Redis 集群的地址。
   * **target.type**：选择目的集群 Redis 的类型。这里的 `standalone` 表示 Redis Standalone 集群，`集群`表示 Redis Cluster 集群。
   * **target.address**：输入目的 Redis 集群的地址。

   >**说明**
   >
   >* 集群类型选择 `standalone` 时对应集群地址需填写 VIP 地址，例如：172.22.4.253:6379
   >* 集群类型选择`集群`时对应集群地址需填写所有节点 IP 地址，例如：172.22.4.2:6379;172.22...;172.22.4.7:6379
   >* 源集群和目的集群的 IP 不可为同一个集群的 IP 地址。
   >* 源集群和目的集群类型可选择相同类型的集群，也可选择不同类型的集群。

2. 点击**更多服务环境参数**并根据实际需求填写。

   以下列出关键参数，其他参数请根据提示填写。

   - **source.password_raw** ：源端密码，留空表示无密码。

   - **target.password_raw**：目标端密码，留空表示无密码。

   - **resume_from_break_point**：断点续传开关。

   - **key_exists**：当源目的有重复 key 时是否进行覆写.

     >**注意**
     >
     >当打开断点续传时, 建议此选项为 `rewrite` 或 `ignore`。

     - `-`: 一旦发生进程直接退出。
     - `rewrite`: 源端覆盖目的端。
     - `ignore`: 保留目的端key，忽略源端的同步 key。

   - qps: 同步QPS上限。

3. 点击**校验表单参数**。

4. 待提示校验成功，点击**提交**。

### 第6步：查看异步复制监控

待 RedisShake 集群创建成功，集群状态为`活跃`，集群节点服务状态为`正常`。在节点页签服务和资源监控页面可查看集群异步复制情况。