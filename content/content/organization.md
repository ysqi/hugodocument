---
aliases:
- /doc/organization/
date: 2016-01-02
linktitle: 组织结构
menu:
  main:
    parent: content
next: /content/supported-formats.html
prev: /overview/source-directory.html
title: 内容组织结构
weight: 10
toc: true
---

Hugo 支持[一些固定格式]({{< relref "content/supported-formats.md" >}})，允许你使用最少的配置来组织内容，在文件头中添加配置能覆盖默认配置。

## 组织结构

在 Hugo内部，应已相同的方式来组织内容在网站中显示。不需要任何额外的配置，下面的结构就能正常使用。Hugo 支持无限级别结构，但最顶层级别在 Hugo 中称之为[专栏]({{< relref "content/sections.md" >}})。

    .
    └── content
        ├── post
        |   ├── firstpost.md   // <- http://1.com/post/firstpost/
        |   ├── happy
        |   |   └── ness.md  // <- http://1.com/post/happy/ness/
        |   └── secondpost.md  // <- http://1.com/post/secondpost/
        └── quote
            ├── first.md       // <- http://1.com/quote/first/
            └── second.md      // <- http://1.com/quote/second/

**下面是使用`hugo --uglyURLs`运行的相同组织结构**

    .
    └── content
        ├── post
        |   ├── firstpost.md   // <- http://1.com/post/firstpost.html
        |   ├── happy
        |   |   └── ness.md    // <- http://1.com/post/happy/ness.html
        |   └── secondpost.md  // <- http://1.com/post/secondpost.html
        └── quote
            ├── first.md       // <- http://1.com/quote/first.html
            └── second.md      // <- http://1.com/quote/second.html

## Destinations

Hugo 相信你所组织的内容结构是有目的地的。相同的结构来组织内容呈现到网站中，正如上面的示例，如何组织内容结构会真实的反应到目的地中。

有些时候，需要更多的控制内容呈现。这个时候，可以在文件头中使用格式各样的参数来决定如何在目的地中呈现内容。

下面是一些有序参数，后面的参数配置会覆盖前面的配置：

### filename
这个不在文件头中定义的。这个内容文件去掉后缀后的真实文件名，也会是在目的地中得文件名。

### slug
在文件头中定义，使用`slug`来重命名目的地中的文件名。

### filepath 
The actual path to the file on disk. Destination will create the destination
with the same path. Includes [section]({{< relref "content/sections.md">}}).

### section
`section` 是在本地磁盘确定的，是顶级文件夹，不能在文件头中定义，具体见 [section]({{< relref "content/sections.md">}})。

### type
`type`也是在本地磁盘中确定的，但不同于`section`，它是可以在文件头中定义的，表示内容所属类型，具体见[type]({{< relref "content/types.md">}}).

### path
`path` can be provided in the front matter. This will replace the actual
path to the file on disk. Destination will create the destination with the same
path. Includes [section]({{< relref "content/sections.md">}})。

### url
定义页面的完整 URL，必需是`/`开头。 定义后，此 URL 为页面的唯一地址，会忽略参数`--uglyURLS`配置。


## Hugo 路径说明

### 内容路径

    .             path           slug
    .       ⊢-------^----⊣ ⊢------^-------⊣
    content/extras/indexes/category-example/index.html


    .       section              slug
    .       ⊢--^--⊣        ⊢------^-------⊣
    content/extras/indexes/category-example/index.html


    .       section  slug
    .       ⊢--^--⊣⊢--^--⊣
    content/extras/indexes/index.html

### 最终页面路径


               permalink
    ⊢--------------^-------------⊣
    http://spf13.com/projects/hugo


       baseURL       section  slug
    ⊢-----^--------⊣ ⊢--^---⊣ ⊢-^⊣
    http://spf13.com/projects/hugo


       baseURL       section          slug
    ⊢-----^--------⊣ ⊢--^--⊣        ⊢--^--⊣
    http://spf13.com/extras/indexes/example


       baseURL            path       slug
    ⊢-----^--------⊣ ⊢------^-----⊣ ⊢--^--⊣
    http://spf13.com/extras/indexes/example


       baseURL            url
    ⊢-----^--------⊣ ⊢-----^-----⊣
    http://spf13.com/projects/hugo


       baseURL               url
    ⊢-----^--------⊣ ⊢--------^-----------⊣
    http://spf13.com/extras/indexes/example



**section** = 默认是内容类型

* 基于内容路径
* 可在文件头中覆盖

**slug** = 文件名.扩展名 或则 文件名/

* 基于  content-文件名.md
* 可在文件头中覆盖

**path** = section + path  不包括 slug

* 基于内容文件路径


**url** = 相对路径

* 可在文件头中电议
* 覆盖上面的设置

