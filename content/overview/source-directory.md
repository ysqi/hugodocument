---
aliases:
- /doc/source-directory/
date: 2013-07-01
menu:
  main:
    parent: getting started
next: /content/organization.html
notoc: true
prev: /overview/configuration.html
title: 源代码组织结构
weight: 50
---

Hugo在一个单独的文件夹下工作，通过文件夹下内容创建一个完整的网站。

源代码文件夹的一级目录通常包含如下文件夹：

    ▸ archetypes/
    ▸ content/
    ▸ data/
    ▸ layouts/
    ▸ static/
    ▸ themes/
      config.toml

不同文件夹用途不同，访问下面内容了解更多：

* [config]({{< relref "overview/configuration.md" >}})
* [data]({{< relref "extras/datafiles.md" >}})
* [archetypes]({{< relref "content/archetypes.md" >}})
* [content]({{< relref "content/organization.md" >}})
* [layouts]({{< relref "templates/overview.md" >}})
* [static]({{< relref "themes/creation.md#toc_4" >}})
* [themes]({{< relref "themes/overview.md" >}})


## Example

一个网站结构示例如下：

    .
    ├── config.toml
    ├── archetypes
    |   └── default.md
    ├── content
    |   ├── post
    |   |   ├── firstpost.md
    |   |   └── secondpost.md
    |   └── quote
    |   |   ├── first.md
    |   |   └── second.md
    ├── data
    ├── layouts
    |   ├── _default
    |   |   ├── single.html
    |   |   └── list.html
    |   ├── partials
    |   |   ├── header.html
    |   |   └── footer.html
    |   ├── taxonomies
    |   |   ├── category.html
    |   |   ├── post.html
    |   |   ├── quote.html
    |   |   └── tag.html
    |   ├── post
    |   |   ├── li.html
    |   |   ├── single.html
    |   |   └── summary.html
    |   ├── quote
    |   |   ├── li.html
    |   |   ├── single.html
    |   |   └── summary.html
    |   ├── shortcodes
    |   |   ├── img.html
    |   |   ├── vimeo.html
    |   |   └── youtube.html
    |   ├── index.html
    |   └── sitemap.xml
    ├── themes
    |   ├── hyde
    |   └── doc
    └── static
        ├── css
        └── js

从这个目录结构可得知网站的大部分信息：

1. 这个网站的内容包含两种类型: *posts* 和 *quotes*.
2. 内容也含有两种分类：*categories* 和 *tags*.
3. 内容显示有三种视图：列表, 摘要 和 全文页。
