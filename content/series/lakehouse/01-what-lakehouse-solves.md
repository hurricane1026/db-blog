---
title: 第 1 篇：Lakehouse 到底在解决什么问题
slug: what-lakehouse-solves
url: /lakehouse-series/what-lakehouse-solves/
date: 2026-04-05
draft: false
categories:
  - 数据平台
tags:
  - Lakehouse
  - 数据平台
  - 架构
summary: lakehouse 的核心价值不只是统一存储，而是把数据平台的存储、计算和交付边界重新拆开。
description: 从平台边界而不是产品名词的角度理解 lakehouse，避免把它误当成“更便宜的数据仓库”。
keywords:
  - Lakehouse
  - 数据平台
  - 数据湖仓一体
  - 架构设计
cover:
  image: /covers/lakehouse-01-boundary.svg
  alt: Lakehouse 边界主题封面
  caption: What lakehouse solves
series:
  - Lakehouse 系列
weight: 10
showToc: true
---

# 第 1 篇：Lakehouse 到底在解决什么问题

很多团队一说到 lakehouse，先想到的是“对象存储更便宜”或者“统一批流查询”。这些都属于结果，但不是问题本身。

lakehouse 想解决的核心矛盾，其实是传统数据仓库和数据湖在组织方式上的断层。

传统数仓的优点是治理强、性能稳、交付清晰，但代价往往是成本高、扩展慢、引擎绑定重。数据湖的优点是存储弹性大、接入自由，但问题是治理弱、元数据混乱、数据质量和一致性难控。

lakehouse 试图做的，是把这两边最关键的能力重新拼起来：

- 用更开放的存储层承接数据规模
- 用表格式和元数据层补足治理与事务能力
- 用多引擎接入提高分析与处理灵活性

## 不要把 lakehouse 理解成单一产品

真正需要先理解的是，lakehouse 更像一种平台组合方式，而不是一个单一软件名字。

一个成熟的 lakehouse 通常至少包含：

- 对象存储
- 表格式
- Catalog / Metastore
- 计算引擎
- 编排与质量控制

如果只替换其中一层，比如只把数据搬到对象存储，或者只上 Iceberg，但摄入、权限、质量、消费路径都没变，那通常不算真正完成了 lakehouse 改造。

## 真正应该先问的是你要解决哪类平台问题

在动手之前，更重要的问题通常是：

1. 你是要降存储成本，还是要做多引擎共享。
2. 你是要提升批流处理一致性，还是要改治理模型。
3. 你现有的痛点在 ETL、分析性能，还是在元数据与权限。

如果这些问题没答清楚，后面选技术栈时就会很容易沦为跟风。
