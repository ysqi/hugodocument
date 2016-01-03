---
date: 2013-07-01
linktitle: 类型
menu:
  main:
    parent: content
next: /content/archetypes.html
prev: /content/sections.html
title: 内容类型
weight: 40
toc: true
---

Hugo 完全支持不同的内容类型，一种内容类型有特定的元数据，模板，且能使用`hugo new`命令新建[指定 [模型archetypes]({{< relref "content/archetypes.md">}})的内容。 

一个很好的案例是[Tumblr](https://www.tumblr.com/)需要支持多种内容类型，有不同元数据，呈现方式也不同的照片,转发，文章等等。 

## 指定内容类型

Hugo假设你的网站均是组织在[专题(Sections)]({{< relref "content/sections.md" >}})下，每个专题都有相对应的类型，并且你正在利用这点，则专题下每篇内容都会自动对应到相应的类型。 

或者，你可以在文件头定义参数`type`来指定实际的内容类型。


## 新建指定类型的内容

Hugo能够创建内容片断时，自动在文件头中插入相对应内容类型的元数据。Hugo正是利用[模型]({{< relref "content/archetypes.md">}})来实现的。

创建新的内容片断，格式：

    hugo new relative/path/to/content.md

例如，你想创建一篇`post`专题下的文章，则输入：

    hugo new post/my-newest-post.md


## 新建内容类型

在 Hugo 中创建内容类型是非常简单的。只需要新建定义模板，模型和特有的内容类型视图，Hugo 就能自动调用这些模板，如果没有找到的话，则使用默认模型。

*注意，下面是可选内容:*

### 新建类型目录
在目录`/layouts`下创建已内容类型名称定义的文件夹，内容类型总是单数形式，例如：

    $ mkdir layouts/post

### 新建单内容模板
在类型目录下新建名为`single.html`文件。 例如：

    $ touch layouts/post/single.html

### 新建内容列表模板
在类型目录下新建名为`list.html`文件。例如：

    $ touch layouts/post/list.html

### 新建视图
许多网站呈现内容有多种方式，比如，在一个内容页上显示内容列表，则需要一个单页视图和一个汇总视图。Hugo 不会猜想你想要如何显示内容，但会仅可能的支持你所需要的内容类型视图。这些附近视图均需要存在目录`/layouts/TYPE`下存在相同名称的模板文件。

### 新建对应模型

在目录`/archetypes` 下新建名为<code><em>type</em>.md</code>的模型文件。例如：

    $ touch archetypes/post.md

关于模型archetypes的更多内容请参见[模型文档]({{< relref "content/archetypes.md">}})。
