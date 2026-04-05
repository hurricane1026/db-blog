---
title: Lakehouse 系列总览
slug: lakehouse-series-overview
url: /lakehouse-series/lakehouse-series-overview/
date: 2026-04-05
draft: false
categories:
  - 数据平台
tags:
  - Lakehouse
  - 数据平台
  - 数据湖
series:
  - Lakehouse 系列
weight: 1
summary: 用一组面向工程团队的文章，系统讲清 lakehouse 的边界、表格式、数据摄入、成本控制与治理落地。
description: 先理解 lakehouse 到底解决什么问题，再进入表格式、摄入链路、计算成本和治理等具体主题。
keywords:
  - Lakehouse
  - 数据湖仓一体
  - 数据平台
  - Iceberg
cover:
  image: /covers/lakehouse-overview.svg
  alt: Lakehouse 系列总览封面
  caption: Lakehouse overview
showToc: true
---

# Lakehouse 系列总览

这几年数据平台的讨论里，lakehouse 几乎已经成了绕不过去的词。很多团队提到它时，会把它理解成“把数仓搬到对象存储上”，或者“用一个新表格式替换 Hive 表”。这些理解都不算完全错，但都太窄。

lakehouse 真正带来的变化，不只是底层存储介质或者查询引擎变了，而是数据平台的组织方式变了。存储、计算、元数据、治理、数据交付不再被强绑定在一套系统里，团队开始用更模块化的方式搭平台。

这组文章会围绕五个高频问题展开：

1. lakehouse 到底适合解决什么问题，不适合解决什么问题。
2. Iceberg、Delta Lake、Hudi 这类表格式到底在解决哪一层问题。
3. 批流一体和多引擎接入时，数据摄入链路应该怎么设计。
4. 存储便宜以后，为什么计算和治理成本反而更容易失控。
5. 一个 lakehouse 平台要真正跑到生产环境里，治理与权限边界应该怎么定。

## 适合谁看

- 在做数据平台升级的数据工程团队
- 从传统数仓往对象存储迁移的架构师
- 需要选表格式、编排链路和查询引擎的技术负责人
- 想把数据治理从“工具堆叠”拉回架构层讨论的人

## 建议阅读顺序

先看总览，然后建议按下面顺序读：

1. 概念边界
2. 表格式选择
3. 数据摄入与建模
4. 计算与成本
5. 治理与生产化
