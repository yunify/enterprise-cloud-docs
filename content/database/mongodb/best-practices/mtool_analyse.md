---
title: "mtools 工具分析日志"
description: 本小节主要介绍如何关闭 MongoDB 日志服务。 
keyword: 关闭日志服务,MongoDB,文档数据库,数据库
weight: 25
collapsible: false
draft: false

---

### 现象描述

线上环境 CPU 激增，CPU 使用率为 100% ， 且持续半小时或更长时间，业务受到影响无法正常工作。

### 集群状态

- 连接数正常。
- 当天业务流量相比前几天增加了10%（多了大概10W条请求）。
- 内存占用一直维持在 80-90%。

### 使用 mtools 工具分析日志

使用 mtools 分析工具执行以下查询语句，详细操作请参见 [mtools 工具查询日志](/database/mongodb/best-practices/mtools_log/)。

- 查看超过 10s 的查询

  ```
  mlogfilter mongod.log --slow 10000 
  ```

- 查看所有慢查询并根据频率排序。

  ```
  mloginfo mongod.log --queries --sort count
  ```

### 业务分析

* 存在大量慢查询，大量查询超过150s。
* 大量查询没有使用索引，导致全表扫描。
* 排序字段没有走索引。
* 索引设计不合理，利用率低下（比如：扫描 5 万个文档，结果仅返回 0~10 个文档，所以即使走了索引，查询也消耗了100s 左右）。
* 对某个集合的查询语句不合理，大量的条件重复。
* 存在上万条 TXN 事务日志。

### 分析结果

针对日志分析出**高频**和**耗时较久**的查询集合 A 跟 B，分别在这两张表上创建索引后，CPU 断崖式下降，由此看出 CPU 激增是慢查询导致。

![监控](../../_images/mtool_analyse_01.png)