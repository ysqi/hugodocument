---
date: 2015-12-28
linktitle: 介绍
menu:
  main:
    parent: getting started
next: /overview/quickstart
title: Hugo介绍
weight: 5
---

## 什么是Hugo?
Hugo是一个通用型网站创建框架，技术层面来讲Hugo是一个静态网站生成工具，不需要像
其他动态网站一样用户访问一次时动态生成页面。
Hugo 在你创建内容时便生成页面，Hugo 在写作时便可在本地实时预览。
 
使用 Hugo 生成是非常快速且安全的。Hugo 网站可以部署到任意地方，因为它是静态的，
包括[Heroku][], [GoDaddy][], [DreamHost][],[GitHub Pages][], [Google云][Google Cloud Storage], 
[亚马逊云][Amazon S3] and [CloudFront][], 并且在CDNS下可以正常使用。Hugo 网站
不需要昂贵的运行时环境，如 Ruby，Python ，PHP，JAVA 等等，同时也不依赖于数据库。
全是因为Hugo创建的是静态网页。

[Heroku]: https://www.heroku.com/
[GoDaddy]: https://www.godaddy.com/
[DreamHost]: http://www.dreamhost.com/
[GitHub Pages]: https://pages.github.com/
[Google Cloud Storage]: http://cloud.google.com/storage/
[Amazon S3]: http://aws.amazon.com/s3/
[CloudFront]: http://aws.amazon.com/cloudfront/ "Amazon CloudFront"

我们认为 Hugo是创建网站的理想工具。Hugo提供了快速有力的响应，能够瞬间创建网站和
实时重新生成网站。这当你创建内容设计网站时，是非常有用的且有必要的。

## Hugo有哪些特色?

网站生成器直接将内容转化为HTML文件。而对于大多数“动态网站”来说，当用户访问网页时，
作为HTTP服务器每次都需要重新生成一个新的HTML页面展示给用户。

创建一个动态网页意味着网站服务器需要保证有足够的内存和CPU来有效生成网页，否则的话，
意味着用户需要排队等待网页显示，网页响应时间越长，越影响用户体验。

没人哪个用户愿意长时间的等待，因此动态网站实现将网页缓存起来，当用户访问的网页是已
经缓存的，则直接拷贝缓存文件显示可用户，这样比重新生成网页的方式网页响应时间也变短
很多。

Hugo正是缓存了这些。所有HTML网页生成在你的电脑上，在你复制文件到网站服务器之前，你
可以直接查看它们。由于没有需要动态生成的HTMl网页，所有我们说 Hugo 是一个“静态网站生
成器”

网站部署在HTTP服务器上运行有很多好处，最引人注意的是性能， HTTP服务器善于传输文件。因此你可以有效的利用相对于动态网站所需要的内存和CPU，来部署
你的Hugo网站。

Hugo 用两个组件来帮助你创建和测试网站。

一个是你可能经常使用的内置HTTP服务器。当你运行`hugo server`时，Hugo将你所有的网站内容生成到HTML文件中，同时会在你电脑启动一个HTTP服务。这样你就
可以看到网页的样子。

另一个是当你准备发布网站内容到网站服务器上时，运行`hugo`将使用配置文件中的`baseurl`参
数来重新生成你的网站。 这个参数是必须的，是你网站页面的链接基本地址。

## Hugo有多快?

{{% youtube CdiDYZ51a2o %}}

## Hugo能做什么?
 
技术层面，Hugo采用文件的源目录和模板来创建生成一个完整的网站。

Hugo拥有下列功能特点：

### 基础功能

  * 极速生成 (~1&nbsp;ms/页面)
  * 完全垮平台支持：运行在 <i class="fa fa-apple"></i>&nbsp;Mac OS&nbsp;X, <i class="fa fa-linux"></i>&nbsp;Linux, <i class="fa fa-windows"></i>&nbsp;Windows,更多!
  * 简易 [安装](/overview/installing/)
  * 写作时[自动更新](/extras/livereload/)，[快速](/overview/usage/)渲染网页
  * 完美的主题支持
  * 可任意地方部署网站

### 组织结构

  * 简约的 [组织结构](/content/organization/)
  * 支持 [网站子目录](/content/sections/)
  * 完全自定义 [URL](/extras/urls/)
  * 支持可配置包含标签和分类的[分类模型](/taxonomies/overview/)， 可自定义属于你的内容组织结构。
  * 按你所期望的方式进行[内容排序](/content/ordering/)
  * 自动生成 [目录](/extras/toc/)
  * 动态创建目录
  * [完美URL](/extras/urls/) 支持
  * 支持[永久链接](/extras/permalinks/) 模式
  * [别名](/extras/aliases/) (重定向)

### 内容功能

  * 原始支持 [Markdown](/content/example/) 写作
    * 通过外部工具支持其他语言, 见[所支持的格式](/content/supported-formats)
  * 支持TOML, YAML and JSON 元数据[格式](/content/front-matter/)
  * 完全[自定义首页](/layout/homepage/)
  * 支持多种 [内容格式](/content/types/)
  * 自动或者自定义[摘要](/content/summaries/)
  * [短代码](/extras/shortcodes/) 方式在Markdown中嵌入富文本
  * ["阅读用时"](/layout/variables/) 功能
  * ["内容字数"](/layout/variables/) 功能

### 附件功能

  * 集成支持 [Disqus](https://disqus.com/) 评论
  * 集成支持 [Google Analytics](https://google-analytics.com/) 
  * 自动生成 [RSS](/layout/rss/)
  * 支持 [Go](http://golang.org/pkg/html/template/), [Amber](https://github.com/eknkc/amber) 以及 [Ace](http://ace.yoss.si/) HTML 语言模板
  * 由[Pygments](http://pygments.org/) 提供语法[高亮](/extras/highlighting/)  

看看接下来还有哪些新功能 [路线图](/meta/roadmap/).

## 谁应该使用 Hugo?

那些喜欢通过浏览器在文本编辑中写作的人。 

那些想要手工编写网站，而不需要为配置复杂的运行时，依赖环境，数据库而担忧的人。  

那些想要创建一个博客，公司网站，作品展，轻博客，文档，单页网站，成千网页的网站的人。

## 为什么写了Hugo?

我写Hugo的根本原因有几点，第一条，我对我的网站使用WordPress非常失望，它响应非常慢，我
没法高效的在线写文章。
The constant security updates and the horror stories of people's hacked blogs. 我讨厌
通过HTML写作，而不用简单的Markdown,总的来说，我觉得我对于我出色写作上得到了更多帮助。

I wrote Hugo ultimately for a few reasons. First, I was disappointed with
WordPress, my then website solution. It rendered slowly. I couldn't create
content as efficiently as I wanted to and needed to be online to write
posts. The constant security updates and the horror stories of people's
hacked blogs. I hated how content was written in HTML instead of the much
simpler Markdown. Overall, I felt like it got in my way more than it helped
me from writing great content.

我看过现有的几个静态网站工具，如 [Jekyll][], [Middleman][] and [nanoc][]。
全部依赖于复杂的安装和长时间的网站生成，生成时间对于我博客上百篇文章还是可以接受的。我想
要一个工具能够在更新模板时能快速重新生成，5分钟左右生成时间实现是太慢了....

I looked at existing static site generators like [Jekyll][], [Middleman][] and [nanoc][].
All had complicated dependencies to install and took far longer to render
my blog with hundreds of posts than I felt was acceptable. I wanted
a framework to be able to get rapid feedback while making changes to the
templates, and the 5+-minute render times was just too slow. In general,
they were also very blog minded and didn't have the ability to have
different content types and flexible URLs.

[Jekyll]: http://jekyllrb.com/
[Middleman]: https://middlemanapp.com/
[nanoc]: http://nanoc.ws/

我想开发一个快速且功能齐全的网站框架而不需要过多依赖。
 [Go 语言][Go language] 看起来能满足我的所有需求，我开始用Go开发Hugo，感觉爱上这么语言了。
 我希望你也想我用Go写Hugo一样喜欢它。

[Go language]: http://golang.org/ "The Go Programming Language"

## 下一步

 * [安装 Hugo](/overview/installing/)
 * [快速引导](/overview/quickstart/)
 * [加入邮件列表](/community/mailing-list/)
 * [在GitHub上评论我们](https://github.com/spf13/hugo)
 * [参与讨论](http://discuss.gohugo.io/)
