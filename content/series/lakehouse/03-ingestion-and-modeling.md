---
title: 第 3 篇：Lakehouse 的数据摄入和建模别只盯着批流一体
slug: lakehouse-ingestion-and-modeling
url: /lakehouse-series/lakehouse-ingestion-and-modeling/
date: 2026-04-05
draft: false
categories:
  - 数据平台
tags:
  - Lakehouse
  - 数据摄入
  - 数据建模
  - 批流一体
summary: lakehouse 的摄入链路重点不只是批流一体，而是怎样让原始层、明细层和消费层之间的责任边界稳定下来。
description: 从原始层、清洗层到消费层拆解 lakehouse 数据摄入与建模，避免把所有复杂度都压给一个统一作业。
keywords:
  - Lakehouse
  - 数据摄入
  - 建模
  - 批流一体
cover:
  image: /covers/lakehouse-03-ingestion.svg
  alt: Lakehouse 数据摄入与建模封面
  caption: Ingestion and modeling
series:
  - Lakehouse 系列
weight: 30
showToc: true
---

# 第 3 篇：Lakehouse 的数据摄入和建模别只盯着批流一体

很多团队做 lakehouse 时，最容易被“批流一体”四个字带偏。因为这个词听起来很高级，仿佛只要把一套链路同时支持 batch 和 stream，平台升级就完成了。

但在真实工程里，决定系统稳定性的往往不是批流一体本身，而是数据层级和责任边界有没有拆清楚。

## 数据摄入最怕一层写到底

一个常见错误是：把所有逻辑都压进同一层作业里，原始接入、清洗、去重、宽表拼接、质量修复、消费输出全放一起。

这样短期看起来省事，长期问题会非常大：

- 某一层变更会牵连整条链路
- 回放和补数边界很难定义
- 数据质量问题不容易定位到哪一层
- 成本和资源消耗难以归因

更稳的做法通常还是分层：

- Raw / Bronze：承接原始事实
- Clean / Silver：处理标准化与基础质量
- Serving / Gold：面向分析和消费输出

## 建模要跟消费路径绑定

lakehouse 的建模如果只从存储角度出发，很容易做成“表很多，但没人会用”。

真正应该一起设计的是：

1. 谁来消费这份数据。
2. 查询延迟要求是什么。
3. 是要支持反复回放，还是要稳定服务报表。
4. 哪些层允许重算，哪些层必须保证稳定输出。

只有把消费路径拉进来，分层和建模才不会停留在漂亮图纸上。
