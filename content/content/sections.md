---
date: 2013-07-01
menu:
  main:
    parent: content
next: /content/types.html
notoc: true
prev: /content/front-matter.html
title: 专栏Sections
weight: 30
---

Hugo 相信你所组织的内容结构是有目的地的。相同的结构来组织内容呈现到网站中，正如上面的示例，如何组织内容结构会真实的反应到目的地中,具体见[ 目录组织结构]({{< relref "content/organization.md" >}})。下面可看到在内容目录结构中顶级目录是是作为**专栏(Sections)** ，这个示例中有两个专栏，分别是 "post" and "quote"。

{{< nohighlight >}}.
└── content
    ├── post
    |   ├── firstpost.md       // <- http://1.com/post/firstpost/
    |   ├── happy
    |   |   └── ness.md        // <- http://1.com/post/happy/ness/
    |   └── secondpost.md      // <- http://1.com/post/secondpost/
    └── quote
        ├── first.md           // <- http://1.com/quote/first/
        └── second.md          // <- http://1.com/quote/second/
{{< /nohighlight >}}

## Section 列表

Hugo 自动为所有专题创建内容页列表。具体见 [列表模板]({{< relref "templates/list.md" >}})自定义设置列表页。

## 专题和类型

默认情况下，节点下内容创建时都使用和类型相匹配的专题。 

专题也可定义在文件头中。

要改变一个给定的内容类型，只需要在文件头中定义`type`。

如果没有提供给定类型的布局文件，则使用默认模板。


