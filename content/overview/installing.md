---
aliases:
- /doc/installing/
date: 2013-07-01
menu:
  main:
    parent: getting started
next: /overview/usage.html
prev: /overview/quickstart.html
title: 安装Hugo
weight: 20
---

Hugo 使用[Go][]开发实现，天然支持跨平台。

可以从Github下载[最新Hugo安装包][ReleaseDownHome]。
当前我们为多个平台编译了x64,i386以及其他架构的版本：

<i class="fa fa-windows"></i>&nbsp;Windows,
<i class="fa fa-linux"></i>&nbsp;Linux,
<i class="fa freebsd-19px"></i>&nbsp;FreeBSD
and <i class="fa fa-apple"></i>&nbsp;OS&nbsp;X (Darwin)

同时也可直接将 Hugo 源代码使用Go 编译器编译安装，如编译到其他操作系统：DragonFly BSD, OpenBSD, Plan&nbsp;9 and Solaris. 具体参考http://golang.org/doc/install/source  是 Go所支持的目标环境。

## 安装包 安装 Hugo

使用使用安装包安装时非常容易的，直接从Github下载对应操作系统的[Hugo安装包](https://github.com/spf13/hugo/releases).
下载后就可以直接运行使用，不需要安装到特殊的固定位置，这对于没有特殊权限的共享主机和其他一些操作系统来说是非常方便有用的。 

当然最方便的是将 Hugo 安装包放到环境变量`PATH`路径中，这样就可以直接使用Hugo 命令。
一般`/usr/local/bin`是常见的安装包保存目录。

对于苹果电脑，如果你有安装[Homebrew](http://brew.sh/)工具，则可以直接运行`brew install hugo`命令安装。

更具体的安装说明，见相应的安装帮助文档： 

- [在苹果电脑安装]({{< relref "tutorials/installing-on-mac.md" >}})
- [在Windows安装]({{< relref "tutorials/installing-on-windows.md" >}})

### 安装 Pygments (可选)

Hugo有一个可选项配置是依赖于语法高亮插件 Pygments。

如果你想在文档中使用[语法高亮扩展功能]({{< relref "extras/highlighting.md">}})，那么你就需要安装基于Python开发的Pygments程序。Pygments使用见[Pygments官网](http://pygments.org/)。

## 更新 Hugo

直接重新下载[最新的 Hugo 安装包][ReleaseDownHome]覆盖原 Hugo 执行文件即可。


## 从源码安装 Hugo

### 下载按照前必备工具

* [Git](http://git-scm.com/)
* [Mercurial](http://mercurial.selenic.com/)
* [Go][] 1.3+ (Go 1.4+ on Windows, see Go [Issue #8090](https://code.google.com/p/go/issues/detail?id=8090))，建议直接安装 Go 最新版本。

### 直接从GitHub获取源代码

    $ export GOPATH=$HOME/go
    $ go get -v github.com/spf13/hugo

`go get` 将获取 Hugo 和所依赖包到你本地`$GOPATH/src` 目录,最终在`$GOPATH/bin/`编译成执行程序`hugo`(or `hugo.exe`)，准备就绪！

你可以使用参数`-u`运行命令`go get`来更新 Hugo

    $ go get -u -v github.com/spf13/hugo

## 为 Hugo 做贡献

请参见 [Hugo贡献说明](/doc/contributing/).

[Go]: http://golang.org/
[ReleaseDownHome]: https://github.com/spf13/hugo/releases
