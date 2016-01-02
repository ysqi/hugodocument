---
aliases:
- /doc/configuration/
date: 2013-07-01
menu:
  main:
    parent: getting started
next: /overview/source-directory.html
notoc: true
prev: /overview/usage.html
title: Hugo配置
weight: 40
toc: true
---

网站目录结构和模板已经提供了大部分网站配置。

实际上，对于大部分常规格式的网站来说甚至是不需要配置文件的。

这个配置文件是网站层面的配置，配置文件能更好的指导 Hugo 如何根据一些参数和菜单来创建一个网站。 

## 例如

下面是 yaml 格式的配置文件样例：

    ---
    baseurl: "http://yoursite.example.com/"
    ...

下面是 含大部分默认值的 toml 格式配置文件。 参数配置写在`[params]`下，在模板中可通过`.Site.Params`访问参数值，如`{{.Site.Params.author}}`。

    contentdir = "content"
    layoutdir = "layouts"
    publishdir = "public"
    builddrafts = false
    baseurl = "http://yoursite.example.com/"
    canonifyurls = true
    
    [taxonomies]
      category = "categories"
      tag = "tags"
    
    [params]
      description = "Tesla's Awesome Hugo Site"
      author = "Nikola Tesla"

再提供一个包含更多配置信息的 yaml 格式配置文件：

    ---
    baseurl: "http://yoursite.example.com/"
    title: "Yoyodyne Widget Blogging"
    footnotereturnlinkcontents: "↩"
    permalinks:
      post: /:year/:month/:title/
    params:
      Subtitle: "Spinning the cogs in the widgets"
      AuthorName: "John Doe"
      GitHubUser: "spf13"
      ListOfFoo:
        - "foo1"
        - "foo2"
      SidebarRecentLimit: 5
    ...

## 参数配置

下面是 Hugo 内部定义的可在配置文件中修改的参数，下面是默认值：

    ---
    archetypedir:               "archetype"
    # 网站根地址, 如： http://hugo.yushuangqi.com
    baseURL:                    ""
    # 是否编译时包括草稿内容
    buildDrafts:                false
    # 是否编译时包括需再以后发布的内容
    buildFuture:                false
    # enable this to make all relative URLs relative to content root. Note that this does not affect absolute URLs.
    relativeURLs:               false
    canonifyURLs:               false
    # 配置文件路径 (默认是 path/config.yaml|json|toml)
    config:                     "config.toml"
    contentdir:                 "content"
    dataDir:                    "data"
    defaultExtension:           "html"
    defaultLayout:              "post"
    # filesystem path to write files to
    destination:                ""
    disableLiveReload:          false
    # Do not build RSS files
    disableRSS:                 false
    # Do not build Sitemap file
    disableSitemap:             false
    # edit new content with this editor, if provided
    editor:                     ""
    footnoteAnchorPrefix:       ""
    footnoteReturnLinkContents: ""
    languageCode:               ""
    layoutdir:                  "layouts"
    # Enable Logging
    log:                        false
    # Log File path (if set, logging enabled automatically)
    logFile:                    ""
    # "yaml", "toml", "json"
    metaDataFormat:             "toml"
    newContentEditor:           ""
    # Don't sync modification time of files
    noTimes:                    false
    paginate:                   10
    paginatePath:               "page"
    permalinks:
    # Pluralize titles in lists using inflect
    pluralizeListTitles:        true
    # Preserve special characters in taxonomy names ("Gérard Depardieu" vs "Gerard Depardieu")
    preserveTaxonomyNames:      false
    publishdir:                 "public"
    # color-codes for highlighting derived from this style
    pygmentsStyle:              "monokai"
    # true: use pygments-css or false: color-codes directly
    pygmentsUseClasses:         false
    # default sitemap configuration map
    sitemap:
    # filesystem path to read files relative from
    source:                     ""
    staticdir:                  "static"
    # display memory and timing of different steps of the program
    stepAnalysis:               false
    # theme to use (located in /themes/THEMENAME/)
    theme:                      ""
    title:                      ""
    # if true, use /filename.html instead of /filename/
    uglyURLs:                   false
    # Do not make the url/path to lowercase
    disablePathToLower:         false
    # if true, auto-detect Chinese/Janapese/Korean Languages in the content. (.Summary and .WordCount can work properly in CJKLanguage)
    hasCJKLanguage              false
    # verbose output
    verbose:                    false
    # verbose logging
    verboseLog:                 false
    # watch filesystem for changes and recreate as needed
    watch:                      false
    ---

## 编译时忽略文件

下面是配置在`config.toml`，使用`hugo`编译时将忽略已`.foo` 和 `.boo` 结尾的文件：

```
ignoreFiles = [ "\\.foo$", "\\.boo$" ]
```

上面是定义的是一个正则表达式列表，但需要注意在 TOML 格式配置文件中需要将**转义符**`\`转换为普通字符，`\\`。



## 配置 Blackfriday 渲染

[Blackfriday](https://github.com/russross/blackfriday) 是 Hugo内默认的[Markdown](http://daringfireball.net/projects/markdown/) 转换工具。 Blackfriday 的配置信息大部分已在 Hugo 中设置了默认值。 

但是 Hugo 也对外提供了些和Blackfriday的([html.go](https://github.com/russross/blackfriday/blob/master/html.go) 和 [markdown.go](https://github.com/russross/blackfriday/blob/master/markdown.go)) 相匹配的标志，如下：

<table class="table table-bordered">
<thead>
<tr>
<th>Flag</th><th>Default</th><th>Blackfriday flag</th>
</tr>
</thead>

<tbody>
<tr>
<td><code><strong>smartypants</strong></code></td>
<td><code>true</code></td>
<td><code>HTML_USE_SMARTYPANTS</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Enable/Disable smart punctuation substitutions such as smart quotes, smart dashes, etc.
May be fine-tuned with the <code>angledQuotes</code>, <code>fractions</code>, <code>smartDashes</code> and <code>latexDashes</code> flags below.</td>
</tr>

<tr>
<td><code><strong>angledQuotes</strong></code></td>
<td><code>false</code></td>
<td><code>HTML_SMARTYPANTS_ANGLED_QUOTES</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Enable/Disable smart angled double quotes.<br>
<small><strong>Example:</strong>&nbsp;<code>"Hugo"</code> renders to «Hugo» instead of “Hugo”.</small></td>
</tr>

<tr>
<td><code><strong>fractions</strong></code></td>
<td><code>true</code></td>
<td><code>HTML_SMARTYPANTS_FRACTIONS</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Enable/Disable smart fractions.<br>
<small><strong>Example:</strong>&nbsp;<code>5/12</code> renders to <sup>5</sup>&frasl;<sub>12</sub> (<code>&lt;sup&gt;5&lt;/sup&gt;&amp;frasl;&lt;sub&gt;12&lt;/sub&gt;</code>)<br>
<strong>Caveat:</strong> Even with <code>fractions = false</code>,
Blackfriday would still convert 1/2, 1/4 and 3/4 to ½&nbsp;(<code>&amp;frac12;</code>),
¼&nbsp;(<code>&amp;frac14;</code>) and ¾&nbsp;(<code>&amp;frac34;</code>) respectively,
but only these three.</small></td>
</tr>

<tr>
<td><code><strong>smartDashes</strong></code></td>
<td><code>true</code></td>
<td><code>HTML_SMARTYPANTS_DASHES</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Enable/Disable smart dashes, i.e. turning hyphens into en&nbsp;dash or em&nbsp;dash.<br>
Its behavior can be modified with the <code>latexDashes</code> flag listed below.</td>
</tr>

<tr>
<td><code><strong>latexDashes</strong></code></td>
<td><code>true</code></td>
<td><code>HTML_SMARTYPANTS_LATEX_DASHES</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Choose between LaTeX-style smart dashes and “conventional” smart dashes.<br>
<strong>If <code>true</code>,</strong> <code>--</code> is translated into “&ndash;” (<code>&amp;ndash;</code>), and <code>---</code> is translated into “&mdash;” (<code>&amp;mdash;</code>).<br>
<strong>If <code>false</code>,</strong> <code>--</code> is translated into “&mdash;” (<code>&amp;mdash;</code>), whereas a <em>spaced</em> single hyphen between two words is turned into an en&nbsp;dash, e.g.&nbsp;<code>12 June - 3 July</code> becomes <code>12 June &amp;ndash; 3 July</code>.</td>
</tr>

<tr style="height: 0.5em;"></tr>

<tr>
<td><code><strong>hrefTargetBlank</strong></code></td>
<td><code>false</code></td>
<td><code>HTML_HREF_TARGET_BLANK</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Open external links in a new window/tab.</td>
</tr>

<tr>
<td><code><strong>plainIDAnchors</strong></code></td>
<td><code>false</code></td>
<td><code>FootnoteAnchorPrefix</code> and <code>HeaderIDSuffix</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">If <code>true</code>, then header and footnote IDs are generated without the document ID.<br>
<small><strong>Example:</strong>&nbsp;<code>#my-header</code> instead of <code>#my-header:bec3ed8ba720b9073ab75abcf3ba5d97</code>.</small></td>
</tr>

<tr style="height: 0.5em;"></tr>

<tr>
<td><code><strong>extensions</strong></code></td>
<td><code>[]</code></td>
<td><code>EXTENSION_*</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Use non-default additional extensions.<br>
<small><strong>Example:</strong>&nbsp;Add <code>"hardLineBreak"</code> to use <code>EXTENSION_HARD_LINE_BREAK</code>.</small></td>
</tr>

<tr>
<td><code><strong>extensionsmask</strong></code></td>
<td><code>[]</code></td>
<td><code>EXTENSION_*</code></td>
</tr>
<tr>
<td class="purpose-title">Purpose:</td>
<td class="purpose-description" colspan="2">Extensions in this option won't be loaded.<br>
<small><strong>Example:</strong>&nbsp;Add <code>"autoHeaderIds"</code> to disable <code>EXTENSION_AUTO_HEADER_IDS</code>.</small></td>
</tr>
</tbody>
</table>


**注意**

1. 这些标志在 Hugo v0.15中是区分大小写的！
2. 这些标志必需配置在节点`blackfriday`下，可以配置在**网站配置和页面文件**中。如果你配置在页面文件中将覆盖网站配置文件中的配置，比如：

<table class="table">
<thead>
<tr>
<th>TOML</th><th>YAML</th>
</tr>
</thead>
<tbody>
<tr style="vertical-align: top;">
<td style="width: 50%;"><pre><code>[blackfriday]
  angledQuotes = true
  fractions = false
  plainIDAnchors = true
  extensions = ["hardLineBreak"]
</code></pre></td>
<td><pre><code>blackfriday:
  angledQuotes: true
  fractions: false
  plainIDAnchors: true
  extensions:
    - hardLineBreak
</code></pre></td>
</tr>
</tbody>
</table>
