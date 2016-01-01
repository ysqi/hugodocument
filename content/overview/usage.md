---
aliases:
- /doc/usage/
date: 2016-01-01
menu:
  main:
    parent: getting started
next: /overview/configuration.html
notoc: true
prev: /overview/installing.html
title: Hugo用法
weight: 30
---

 确保下载的`hugo`(或者 `hugo.exe`)所在目录在环境变量`PATH`中存在。在命令窗口执行`hugo help`命令：

{{< nohighlight >}}$ hugo help

hugo is the main command, used to build your Hugo site.

Hugo is a Fast and Flexible Static Site Generator
built with love by spf13 and friends in Go.

Complete documentation is available at http://gohugo.io/.

Usage:
  hugo [flags]
  hugo [command]

Available Commands:
  server      A high performance webserver
  version     Print the version number of Hugo
  config      Print the site configuration
  check       Check content in the source directory
  benchmark   Benchmark hugo by building a site a number of times.
  convert     Convert your content to different formats
  new         Create new content for your site
  list        Listing out various types of content
  undraft     Undraft changes the content's draft status from 'True' to 'False'
  import      Import your site from others.
  gen         A collection of several useful generators.

Flags:
  -b, --baseURL="": hostname (and path) to the root, e.g. http://spf13.com/
  -D, --buildDrafts[=false]: include content marked as draft
  -F, --buildFuture[=false]: include content with publishdate in the future
      --cacheDir="": filesystem path to cache directory. Defaults: $TMPDIR/hugo_cache/
      --canonifyURLs[=false]: if true, all relative URLs will be canonicalized using baseURL
      --config="": config file (default is path/config.yaml|json|toml)
  -d, --destination="": filesystem path to write files to
      --disableRSS[=false]: Do not build RSS files
      --disableSitemap[=false]: Do not build Sitemap file
      --editor="": edit new content with this editor, if provided
      --ignoreCache[=false]: Ignores the cache directory for reading but still writes to it
      --log[=false]: Enable Logging
      --logFile="": Log File path (if set, logging enabled automatically)
      --noTimes[=false]: Don't sync modification time of files
      --pluralizeListTitles[=true]: Pluralize titles in lists using inflect
      --preserveTaxonomyNames[=false]: Preserve taxonomy names as written ("Gérard Depardieu" vs "gerard-depardieu")
  -s, --source="": filesystem path to read files relative from
      --stepAnalysis[=false]: display memory and timing of different steps of the program
  -t, --theme="": theme to use (located in /themes/THEMENAME/)
      --uglyURLs[=false]: if true, use /filename.html instead of /filename/
  -v, --verbose[=false]: verbose output
      --verboseLog[=false]: verbose logging
  -w, --watch[=false]: watch filesystem for changes and recreate as needed

Use "hugo [command] --help" for more information about a command.
{{< /nohighlight >}}

## 常见命令

最常见的命令是直接在网站目录下执行命令`hugo`，信息如下：

{{< nohighlight >}}$ hugo
0 draft content
0 future content
99 pages created
0 paginator pages created
16 tags created
0 groups created
in 120 ms
{{< /nohighlight >}}

该命令生成静态网站到目录`public/`下，你可将生成后的内容发布到你的网站服务器。

## 马上开工开发你的网站

如果你想在写作过程中想立刻看到变化，则可用 Hugo监控。Hugo 将监控文件变化，当你保存文件时 Hugo会快速重新编译网站：

{{< nohighlight >}}$ hugo -s ~/Code/hugo/docs
0 draft content
0 future content
99 pages created
0 paginator pages created
16 tags created
0 groups created
in 120 ms
Watching for changes in /Users/spf13/Code/hugo/docs/content
Press Ctrl+C to stop
{{< /nohighlight >}}

Hugo 甚至可以启动一个 Web 服务器来实时同步预览网站。 
Hugo 实现 [重载](/extras/livereload/) 技术来自动重新刷新你所打开的网页，支持任意启用了 Javas的浏览器，甚至包括移动端浏览器。这是开发 Hugo 网站最简单最常见的方式：

{{< nohighlight >}}$ hugo server -ws ~/Code/hugo/docs
0 draft content
0 future content
99 pages created
0 paginator pages created
16 tags created
0 groups created
in 120 ms
Watching for changes in /Users/spf13/Code/hugo/docs/content
Serving pages from /Users/spf13/Code/hugo/docs/public
Web Server is available at http://localhost:1313/
Press Ctrl+C to stop
{{< /nohighlight >}}


## 部署网站

在通过`hugo server`在本地开发网站后，你最后需要执行不带参数`server`的命令`hugo`来重新编译网站，这样你可通过FTP,SFTP,WebDAN,RSync,Git Push 等将`public`目录下文件发布到网站服务器来部署网站。

在 Hugo 生成静态网站后，你可部署到任何服务器上，比如：[Heroku][], [GoDaddy][], [DreamHost][], [GitHub Pages][], [Amazon S3][] 和 [CloudFront][],  甚至是其他免费静态web服务器。

[Apache][], [Nginx][], [IIS][]...  都是可以部署网站的。

[Apache]: http://httpd.apache.org/ "Apache HTTP Server"
[Nginx]: http://nginx.org/
[IIS]: http://www.iis.net/
[Heroku]: https://www.heroku.com/
[GoDaddy]: https://www.godaddy.com/
[DreamHost]: http://www.dreamhost.com/
[GitHub Pages]: https://pages.github.com/
[Amazon S3]: http://aws.amazon.com/s3/
[CloudFront]: http://aws.amazon.com/cloudfront/ "Amazon CloudFront"


### 部署说明

执行 `hugo` *不会* 在生成网站前删除已存在的文件。这意味着在执行`hugo`命令前你需要清空`public`文件夹下文件或则运行待参数`-d`/`--destination`的命令`hugo`,否则导致残留错误的文件（如：草稿，Future Post）

一个简单的方案是针对开发和发布使用不同的文件目录。

启动 Web 服务器来显示草稿内容，需要添加另一个参数`dev`来启动服务,这样可将开发时的内容实时写到目录`dev/`下，这样就不会污染原`public/`目录。

{{< nohighlight >}}$ hugo server -wDs ~/Code/hugo/docs -d dev
{{< /nohighlight >}}

当你准备发布时，则使用默认目录`public/`:

{{< nohighlight >}}$ hugo -s ~/Code/hugo/docs
{{< /nohighlight >}}

这样就能有效防止还未准备发布的内容被意外发布。

### 或则直接使用 Hugo 运行网站！

你没看错，这是**可行的**！ 因为不管是创建网站还是作为网站服务，Hugo 都是极快的，这得益于 Go语言所支持的并发和多线程，有些用户更喜欢直接使用 Hugo 作为网站服务运行在**生产环境**！

其他 Web 服务器软件 (Apache, Nginx, IIS...)不再是必须的。

运行命令如下：

{{< nohighlight >}}$ hugo server --baseURL=http://yoursite.org/ \
              --port=80 \
              --appendPort=false \
              --bind=87.245.198.50
{{< /nohighlight >}}

注意`bind`是可选择的，用于Web服务器绑定哪个地址（默认绑定到`127.0,0.1`，主要用于开发场景）。大部分主机，如 Amazon WS, 是通过网络跳转的，你很难确定实际的 IP 地址，这时候使用`--bind= 0.0.0.0` 绑定到所有主机。

通过这种方式，实际上你可能只是部署网站源代码，同时用Hugo运行它们。 

这时候，如果你不需要添加重载JS代码到页面，你可以添加参数 `--disableLiveReload=true`  。

有趣吗？ 这样有些 Hugo用户写得不错的入门教程：

* [hugo, syncthing](http://fredix.xyz/2014/10/hugo-syncthing/) (French) by Frédéric Logier (@fredix)

