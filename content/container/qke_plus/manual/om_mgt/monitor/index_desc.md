---
title: "监控指标说明"
description: QKE 支持的监控
draft: false
keyword: QKE,监控,指标
weight: 1
---

QKE 提供了基于集群级别及节点级别的监控数据收集与展示。通过监控数据，您可以快速查看集群及节点的资源使用情况。

## 集群监控指标

**资源使用情况指标：**

| 监控项 | 指标含义                             |
| :----- | :----------------------------------- |
| CPU    | 统计 CPU 的使用率、已使用量及总量。  |
| 内存   | 统计内存的使用率、已使用量及总量。   |
| 容器组 | 统计容器组的使用率、已使用量及总量。 |
| 存储   | 统计存储的使用率、已使用量及总量。   |

## 节点监控指标

| 监控项     | 监控周期 | 单位 | 指标含义                                                     |
| :--------- | :------- | :--- | :----------------------------------------------------------- |
| CPU 用量   | 5分钟    | %    | 统计 CPU 使用率。                                            |
| 内存用量   | 5分钟    | %    | 统计内存使用率。                                             |
| 磁盘吞吐量 | 5分钟    | KB/s | 统计硬盘每秒读取及写入速率，可分别获取从硬盘读取或写入硬盘的速率。 |
| 磁盘 IOPS  | 5分钟    | 次   | 统计硬盘每秒读取或写入次数，可分别获取从硬盘读取或写入硬盘的次数。 |



