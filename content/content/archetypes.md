---
date: 2014-05-14T02:13:50Z
menu:
  main:
    parent: content
next: /content/ordering.html
prev: /content/types.html
linkTitle: 模型
title: 内容模型archetype
weight: 50
toc: true
---

Hugo v0.11 介绍了内容创建概念，使用命令<code>hugo new <em>[内容文件相对路径]</em></code> 新建内容文件，内容文件将自动配置日期和标题。这是很受欢迎的功能，但经常写作的人来说还远远不够。 

当你执行`hugo new`命令新建内容文件时，Hugo自动的在文件头中填充信息，这是 Hugo 内容模型的概念。


## 示例

### 第一步. 新建内容模型

在这个示例需求中，我们给一个博客写博文，文章类型为 blog post。同时还需给博文预定义标签tags和分类categories。

如下：

#### archetypes/default.md

```toml
+++
tags = ["x", "y"]
categories = ["x", "y"]
+++
```

> __⚠️警告:__  有效编辑器 (如： Sublime, Emacs) 是不在文件末行上插入行尾结束符EOF的的。如果执行`hugo new`命令时出现 [strange EOF error](/troubleshooting/strange-eof-error/)错误，请打开内容模型文件 (即，&nbsp;`archetypes/*.md`)， 必需在结束符`+++`或者`---`后面按下<kbd>Enter</kbd>键。


### 第二步，使用内容模型

前面我们已新建内容模型`archetypes/default.md`，我们就可以直接在专题`post`下使用`hugo new`新建博文。

    $ hugo new post/my-new-post.md

此时，Hugo会新建一个如下内容的文件：

#### content/post/my-new-post.md

```toml
+++
title = "my new post"
date = "2015-01-12T19:20:04-07:00"
tags = ["x", "y"]
categories = ["x", "y"]
+++
```

我们看到`title` 和 `date` 元数据被添加，而扩展的元数据 `tags` 和 `categories` 也通过内容模型`archetype/default.md`被添加。

恭喜您，我们已成功创建了内容模型，并且将之使用在新内容上。但是，如果想在其他类型的内容上使用不同的元数据该怎么办呢？ 比如：音乐内容？当然没问题！

### 第三步，新建自定义内容模型

以前的方式是，我们在 content 目录下新建子文件夹来添加内容文件。这样的话，新建内容应该是`content/musician`。新建内容文件时，便在`archetypes`目录下找到相匹配的内容模型`musician.md`来初始化新建内容文件。此时，你只需要在`archetypes`新建内容模型`musician`即可。

一个简单示例： 

#### archetypes/musician.md

```toml
+++
name = ""
bio = ""
genre = ""
+++
```

用此内容模型新建内容页：

    $ hugo new musician/mozart.md

此时Hugo 找到自定义的内容模型文件使用默认元数据新建内容页。因此刚生成的内容页包含元数据`name`, `bio` 和 `genre`：

#### content/musician/mozart.md

```toml
+++
title = "mozart"
date = "2015-08-24T13:04:37+02:00"
name = ""
bio = ""
genre = ""
+++
```

## 文件头使用其他格式

默认情况下，新建内容页的文件头使用TOML 格式，而不会使用内容模型的内容格式。

但你可以在网站配置文件（`config.toml`）中参数`MetaDataFormat`来指定默认的文件头格式。 所支持文件头格式有：`"toml"`, `"yaml"` and `"json"`。


## 哪个内容模型被使用？

规则如下：

* 如果`archetypes`目录下存在和内容类型名称相匹配的内容模型文件，则使用该内容模型。
* 如果没有找到，则使用默认的内容模型`archetypes/default.md`。
* 否则的话，则在所使用的主题下查找：
    * 如果`archetypes`目录下存在和内容类型名称相匹配的内容模型文件，则使用该内容模型。
    * 如果没有找到，则使用默认的内容模型`archetypes/default.md`
* 如果上面都没有找到内容模型文件，则使用 Hugo内部携带的内容模型。

Hugo 提供一个仅包含元数据 `title`（基于文件名) 和 `date` （ RFC&nbsp;3339 标准的当前时间
[`now()`](http://golang.org/pkg/time/#Now) ）的简单内容模型。

> *注意: `hugo new` 不会在使用自定义内容模型新建的内容文件中自动添加元数据`draft = true`。这个故意这样设计的，原因是内容默认元数据信息应该完全由内容模型来决定。*     
> *当然对于每个内容文件来说，因元数据`title`和`date`是动态必须的，这是个特例设计。*

内容类型是根据文件路径自动检测的。欢迎在新建时使用`--kind`标志使用哪个内容模型，如：
    
    $ hugo new post/my-share-music.md --kind musician
