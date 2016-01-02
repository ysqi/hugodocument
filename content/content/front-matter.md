---
aliases:
- /doc/front-matter/
date: 2013-07-01
menu:
  main:
    parent: content
next: /content/sections.html
prev: /content/organization.html
title: 文件头
weight: 20
toc: true
---

这个**w文件头**是 Hugo 一大特色功能。它允许你定义些内容元数据在文件头中。Hugo 支持不同格式的文件头，每个都有唯一标记。 

所支持的文件头格式

  * **[TOML][]**, 标记符'`+++`'。
  * **[YAML][]**, 标记符'`---`'。
  * **[JSON][]**, 用`{`和`}`各占一行包含的一个 JSON 对象。

[TOML]: https://github.com/toml-lang/toml "Tom's Obvious, Minimal Language"
[YAML]: http://www.yaml.org/ "YAML Ain't Markup Language"
[JSON]: http://www.json.org/ "JavaScript Object Notation"

## TOML 示例

<pre><code class="language-toml">+++
title = "spf13-vim 3.0 release and new website"
description = "spf13-vim for vim."
tags = [ ".vimrc", "plugins", "spf13-vim", "vim" ]
date = "2012-04-06"
categories = [
  "Development",
  "VIM"
]
slug = "spf13-vim-3-0-release-and-new-website"
+++
</code><code class="language-markdown">Content of the file goes Here
</code></pre>

## YAML 示例

```yaml
---
title: "spf13-vim 3.0 release and new website"
description: "spf13-vim for vim."
tags: [ ".vimrc", "plugins", "spf13-vim", "vim" ]
date: "2012-04-06"
categories:
  - "Development"
  - "VIM"
slug: "spf13-vim-3-0-release-and-new-website"
---

Content of the file goes Here
```

## JSON 示例

```json
{
    "title": "spf13-vim 3.0 release and new website",
    "description": "spf13-vim for vim.",
    "tags": [ ".vimrc", "plugins", "spf13-vim", "vim" ],
    "date": "2012-04-06",
    "categories": [
        "Development",
        "VIM"
    ],
    "slug": "spf13-vim-3-0-release-and-new-website",
}

Content of the file goes Here
```

## 变量

一些需要使用的变量是预定义的，用户也可以自己定义任何想要的变量。在模板中通过`.Params`来访问自定义变量。变量总是被转换为成小写，比如定义`camelCase: true`变量，通过`.Params.camelcase`访问。

### 必备变量

* **title** 内容标题
* **description** 内容描述信息
* **date** 用于排序使用的文件日期。
* **taxonomies** 一组用于检索的分类标签(见上面的 tags 和 categories)

### 可选变量

* **aliases**  一组文件别名。
              (e.g. old published path of a renamed content)
              别名访问会重定向到文件实际位置。具体参见 [Aliases]({{< relref "extras/aliases.md" >}})
* **draft** 如果为 ture，则内容不会被发布，除非命令`hugo`携带`--buildDrafts`参数。
* **publishdate** 如果是以后的日期，则内容不会被发布，除非命令`hugo`携带`--buildFuture`参数
* **type** 内容类型，如果不设置则自动从文件目录中提取。
* **isCJKLanguage** 如果为 true，则指明内容为 CJKLanguage 。此时 .Summary 和.WordCount 才能正确显示。
* **weight** 内容排序权重。
* **markup** *(Experimental)* Specify `"rst"` for reStructuredText (requires
            `rst2html`) or `"md"` (default) for Markdown
* **slug** 生成 URL 的结尾部分。
* **url** 针对网站根目录的完整相对路径<br>

*如果`slug` 和 `url` 都不指定, 则使用 filename*

## 配置 Blackfriday 渲染方式

可以在文件头中配置Markdown 渲染的一些参数信息，这将覆盖网站配置文件配置。
详见 [配置文件]({{< ref "overview/configuration.md#配置-blackfriday-渲染" >}}) for more.

