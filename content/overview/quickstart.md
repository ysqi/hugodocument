---
date: 2013-07-01
linktitle: 快速入门
menu:
  main:
    parent: getting started
next: /overview/installing.html
prev: /overview/introduction.html
title: Hugo 快速入门
weight: 10
---

> _注意: 本文章基于 Hugo v0.11写作，如果你使用的更早的 Hugo 版本，请在开始前先[升级]((/overview/installing/) Hugo。_

{{% youtube w7Ft2ymGmfc %}}

## 第一步， 安装 Hugo

到 Github 下载你符合你操作系统的[Hugo安装包](https://github.com/spf13/hugo/releases)。

将安装包保存为文件名`hugo` (Window 下是`hugo.exe`)。

更多的安装细节见 [Hugo安装指引](/overview/installing/)。

## 第二步， 使用 Hugo 新建网站

使用Hugo能新建一个清晰简单结构的网站：

    $ hugo new site /path/to/site

`/path/to/site`是你指定的网站存放位置，注意下面所有的命令都是直接在网站目录下执行：

    $ cd /path/to/site

刚新建网站目录结构如下：

      ▸ archetypes/
      ▸ content/
      ▸ data/
      ▸ layouts/
      ▸ static/
        config.toml

目前新建网站还是没有任何具体内容的，且没有进行任何配置，继续往下看。

## 第三步， 添加些内容

>  如果你用过类似的工具，如 Jekyll,Ghost 或者 Wordpress ，而又想将内容迁移过来的话，可参见列表：[ 迁移工具]({{< relref "tools/index.md#migration-tools" >}})。

Hugo 轻松的创建一个内容页面：

    $ hugo new about.md

此时会在目录`content/` 下新建一个文件，文件名为`about.md`,文件内容如下:

```
+++
date = "2015-01-08T08:36:54-07:00"
draft = true
title = "about"

+++

```

注意元数据`date`是在新建时自动填写的文件创建日期。

直接在符号`+++`后面编辑 Markdown 格式内容。
例如：

```markdown
## A headline

Some Content
```

更有趣的方式是，你可直接新建文档到其他文章：

    $ hugo new post/first.md

上面文件位置是 `content/post/first.md`。

接着我们可以使用一些主题模板来展示网站内容。

## 第四步， 安装Hugo主题

Hugo 拥有丰富的主题，越来越多的主题可供你选择，你可以一次性安装 Hugo 所有的最新主题， 只需要直接拷贝 **hugoThemes**库到网站目录下即可：

```bash
$ git clone --depth 1 --recursive https://github.com/spf13/hugoThemes.git themes
```

如果网速不太好，也可以[选择下载一个 Hugo 主题](http://themes.gohugo.io)，如：
```bash
$ mkdir themes
$ cd themes
$ git clone git@github.com:digitalcraftsman/hugo-icarus-theme.git icarus 
```

## 第五步， 运行 Hugo

Hugo本身就含有高性能的 Web 服务器，直接运行 `hugo server` Hugo 使用本地的一个端口启动 Web 服务器，具体信息如下：

    $ hugo server --theme=icarus --buildDrafts
    2 of 2 drafts rendered
    0 future content
    2 pages created
    0 paginator pages created
    0 tags created
    0 categories created
    in 15 ms
    Watching for changes in /home/user/exampleHugoSite/{data,content,layouts,static,themes}
    Serving pages from memory
    Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
    Press Ctrl+C to stop

上面命令我们使用了两个可选参数，如下:

 * `--theme` 表示使用哪个主题，`icarus`是目录`themes/`下的主题文件夹名称;
 * `--buildDrafts` 表示草稿内容也一块显示，我们上面刚新建的内容，默认是草稿`draft = true`

了解更多 Hugo 的参数信息，执行如下命令：

    $ hugo help

想了解启动 Hugo 实时预览模式的参数信息，执行如下命令：

    $ hugo help server

## 第六步， 编辑内容

Hugo 不仅仅是启动一个 Web 服务，同时它还可以实时监控文件变化，自动重新刷新打开的页面，这样就可以边编辑修改边实时同步预览，它还可以在手机浏览器上实时预览。 

同时按<kbd>Ctrl</kbd>+<kbd>C</kbd>键直接停止 Hugo. 运行信息如下：

    $ hugo server --theme=hyde --buildDrafts
    2 pages created
    0 tags created
    0 categories created
    in 5 ms
    Watching for changes in exampleHugoSite/content
    Serving pages from exampleHugoSite/public
    Web Server is available at http://localhost:1313
    Press Ctrl+C to stop

打开你钟爱的[编辑器](http://vim.spf13.com/), 编辑保存内容，Hugo 监控变化会自动更新。

你一保存，浏览器立刻自动刷新显示，这是非常高效的，一眨眼间Hugo就飞快地更新建立网站，你都不需要等待多久，在编辑器和浏览器切换间，页面就已经被自动更新。 

当你保存文件后，你可看写打屏信息：

    Change detected, rebuilding site
    2015-11-27 15:13 +0100
    2 of 2 drafts rendered
    0 future content
    2 pages created
    0 paginator pages created
    0 tags created
    0 categories created
    in 11 ms

## 第七步， 乐在其中

学习的最好方式是动手实践。

Hugo 实践路线参考：

 * 新增[内容页面](/content/organization/)
 * 新增[节点](/content/sections/)
 * 修改[模板](/layout/templates/)
 * 创建[TOML文件头](/content/front-matter/)的内容页
 * 在[文件头](/content/front-matter/)自定义字段信息
 * 在[模板中显示字段](/layout/variables/)信息
 * 新建[内容类型](/content/types/)
