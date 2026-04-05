---
title: 第 2 篇：Iceberg、Delta Lake、Hudi 该怎么看
slug: lakehouse-table-format-selection
url: /lakehouse-series/lakehouse-table-format-selection/
date: 2026-04-05
draft: false
categories:
  - 数据平台
tags:
  - Lakehouse
  - Iceberg
  - Delta Lake
  - Hudi
summary: 选表格式的关键不在于谁最流行，而在于你的写入模型、查询路径和引擎生态更适合哪一套事务与元数据机制。
description: 从写入模式、读写并发、元数据管理和引擎兼容性四个角度讨论 lakehouse 表格式选择。
keywords:
  - Iceberg
  - Delta Lake
  - Hudi
  - Lakehouse
cover:
  image: /covers/lakehouse-02-format.svg
  alt: Lakehouse 表格式选择封面
  caption: Table format selection
series:
  - Lakehouse 系列
weight: 20
showToc: true
---

# 第 2 篇：Iceberg、Delta Lake、Hudi 该怎么看

很多团队做 lakehouse 选型时，最先卷进去的就是表格式之争。但如果开场白是“谁更先进”，后面通常会越聊越虚。

表格式真正决定的，不只是元数据长什么样，而是你的平台怎么处理下面这些事情：

- 写入提交
- 快照管理
- 小文件合并
- Schema 演进
- 多引擎读写兼容

## 选型先看写入模型

一个非常实用的判断点是：你的主要写入模型是什么。

如果你更多是批处理追加，需求重点在稳定的快照读取和多引擎兼容，那么 Iceberg 往往会是自然候选。

如果你已经在 Spark 生态里深度使用事务和统一平台能力，Delta Lake 的一体化体验会更顺。

如果你的写入高度依赖增量更新、upsert 和近实时导入，Hudi 在一些场景下会更贴近需求。

## 别只看功能表，要看运维模型

同样支持时间旅行、Schema 演进，并不意味着运维成本一样。

真正要多问的包括：

1. 元数据规模上来以后，Catalog 能不能扛住。
2. 小文件治理要不要自己补工具链。
3. 多个引擎同时接入时，兼容边界在哪里。
4. 团队是否有能力理解和处理底层快照、manifest、compaction 这些概念。

选表格式，本质上不是选一个 logo，而是在选未来三年的平台运维模型。
