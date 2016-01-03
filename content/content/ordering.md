---
date: 2014-03-06
linktitle: 排序
menu:
  main:
    parent: content
next: /content/summaries.html
prev: /content/archetypes.html
title: 内容排序
weight: 60
---

Hugo 支持灵活的组织内容顺序。

默认情况下，内容通过权重`weight`排序，然后是时间`date`（最近日期排第一），但也可以选择`title` 和 `linktitle`排序。排序内容被用于[内容列表]({{< relref "templates/list.md">}})模板中。 

_元数据`date` and `weight` 是可选的._

没有权重的内容在列表的最后面。如果没有设置权重或权重一样，则用元数据`date`排序。 如果都没设置，则决定于内容文件从磁盘读取顺序，无法保证稳定的顺序。

## 分配权重

```toml
+++
weight = 4
title = "Three"
date = "2012-04-06"
+++
Front Matter with Ordered Pages 3
```

## 按内容分类信息排序

详见 [分类排序文档]({{< relref "taxonomies/ordering.md">}})。
