---
title: "启停帐号" 
description: 本小节介绍如何启用及停用 ACL 用户。 
keyword: 访问控制，用户管理 ACL,启停帐号,启停 ACL 用户,键值数据库,Redis,Redis Standalone,数据库
weight: 10
collapsible: false
draft: false
---

您可以根据实际需要停用和启用 ACL 用户帐号。

- ACL 用户帐号停用后，帐号将暂时不不能访问 Redis。
- 用户列表**开启/停用**列的值为 `off` 表示帐户为停用状态；`on` 表示帐户为启用状态。

## 约束限制

- 仅 Redis 6.* 及以上版本，支持控制台管理 ACL 用户。
- 不支持停止 **default** 用户帐号。

## 前提条件

- 已获取管理控制台登录账号和密码，且已获取集群操作权限。
- 已创建 Redis Standalone 集群，且集群状态为`活跃`。
- 已创建 ACL 用户帐号。

## 操作步骤

1. 登录管理控制台。
2. 选择**产品与服务** > **数据库与缓存** > **键值数据库 Redis Standalone**，进入集群管理页面。
3. 选择目标集群，点击目标集群 ID，进入集群详情页面。
4. 点击**用户管理 ACL**页签，进入集群用户管理页面。
5. 找到目标用户，点击**操作**列的**开/关用户**，弹出配置窗口。

   <img src="../../../_images/off_and_on_user.png" alt="启停用户" style="zoom:50%;" />

6. 在**开启/停用**参数右侧的下拉框中，选择**开启**或**关闭**。
7. 点击**提交**，返回用户列表。

   集群状态为`更新中`，待状态变为`活跃`即修改成功。
