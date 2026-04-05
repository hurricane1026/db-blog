---
title: 第 4 篇：Lakehouse 成本问题往往不在存储
slug: lakehouse-compute-and-cost
url: /lakehouse-series/lakehouse-compute-and-cost/
date: 2026-04-05
draft: false
categories:
  - 成本治理
tags:
  - Lakehouse
  - 成本优化
  - 计算成本
  - 数据平台
summary: lakehouse 平台真正容易失控的，通常不是对象存储费用，而是扫描量、重复计算和治理缺失带来的计算成本。
description: 从扫描量、文件组织、引擎并发和治理边界四方面分析 lakehouse 的成本控制。
keywords:
  - Lakehouse
  - 计算成本
  - 成本优化
  - 数据平台
cover:
  image: /covers/lakehouse-04-cost.svg
  alt: Lakehouse 计算与成本封面
  caption: Compute and cost
series:
  - Lakehouse 系列
weight: 40
showToc: true
---

# 第 4 篇：Lakehouse 成本问题往往不在存储

很多团队上 lakehouse，一个很强的动机是“对象存储更便宜”。这件事本身没错，但如果因此认为总体成本会自然下降，通常会低估后面的复杂度。

因为平台一旦进入生产规模，真正容易失控的往往不是存储费，而是：

- 查询扫描量
- 重复计算
- 小文件带来的额外元数据与执行开销
- 多引擎并发下的资源竞争

## 存储便宜，会放大不良使用习惯

对象存储的便宜有一个副作用：团队更容易对数据膨胀变得麻木。

表看起来都放得下，于是：

- 分区设计随意
- 历史数据很少回收
- 衍生表越堆越多
- 临时计算结果没人清理

这时候问题不会先出在账单第一行，而是先出在查询引擎和编排链路上。

## 成本治理一定要拉上治理模型一起做

如果平台只看资源账单，不看数据产品和权限边界，优化很容易失焦。

真正更有效的做法通常是：

1. 建立数据集和作业的责任归属。
2. 给扫描量、计算时长和失败重跑做归因。
3. 约束临时表、派生表和历史快照生命周期。
4. 把“能不能读”与“值不值得算”一起管理。

lakehouse 成本治理，本质上是平台治理问题，不只是账单问题。
