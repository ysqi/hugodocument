---
aliases:
- /doc/supported-formats/
date: 2016-01-02
menu:
  main:
    parent: content
next: /content/front-matter.html
prev: /content/organization.html
title: 支持的内容格式
weight: 15
toc: false
---

  自0.14版本，Hugo 提供个称之为_external helpers_的新概念，意味着你可以写 Asciidoc[tor] 文件格式的内容。当前 Hugo 支持的内容格式有markdown,asciidoc,,mmark,rst,html([查看更多](https://github.com/spf13/hugo/blob/77c60a3440806067109347d04eb5368b65ea0fe8/helpers/general.go#L65)), 只有文件类型符合所支持的内容格式，则会按照对应模式生成内容。

  这意味着你本机必需按照对应的工具来生成对应格式的内容。 

  比如，对于 Asciidoc 文件, Hugo 将尝试调用__asciidoctor__ 或 __asciidoc__ 命令。

  使用这些格式，仅需要用标准文件格式，the front matter exactly as you would do with natively supported _.md_ files.

  注意：

  * 作为外边命令，内容生成性能很大程度依赖这些外部工具。
  * 这些功能还刚推出，欢迎反馈信息。
