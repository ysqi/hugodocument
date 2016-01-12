---
author: "Michael Henderson"
date: 2015-02-22
linktitle: Mac上安装
toc: true
menu:
  main:
    parent: tutorials
next: /tutorials/installing-on-windows.html
prev: /tutorials/github-pages-blog.html
title: 在Mac上安装Hugo
weight: 10
---

# 在Mac上安装Hugo

本教程将指导在Mac电脑上安装Hugo。

## 前提

1. 你知道如何打开  terminal 窗口.
2. 你Mac电脑是64位的。
3. 使用目录  `~/Sites`工作。

## 选择不同安装方式

有三种方式在Mac电脑上安装Hugo： 通过`brew` 工具, 安装包, 或者从源代码安装。
没有哪种是最好的方式，选择合适你的。 

每种方式的优缺点：

1. `Brew`简单简洁，轻微缺点。默认包是最新版本，近期Bug修改之后包含在下一个版本中。当然可以通过选项`--HEAD`来按照开发版。更新到`brew`的版本日期和Hugo时间新版本发布日期有点延迟，因为会涉及其他的协同修改。如果你希望使用一个稳定，大量使用的版本，我还是推荐使用`brew`。这种方式运行正常稳定，更新版本容易。

2. 安装包下载安装也非常容易。你只需要执行几个命令，就能完成。更新也容易，重新下载覆盖即可。这样可以让你在电脑上同时使用多个版本的Hugo，如果你不喜欢使用`brew`，使用二进制安装包也是一种不错的选择。

3. 从源码编译安装也是可以的。这样的好处是你不需要等待一个新功能或者Bug修复的新版本，缺点是你需要比前面两者更多的时间来管理安装

由于这是入门教程，我会更多时间详细介绍前面两种安装方式 。

## 从Brew安装

### 第一步：安装``Brew

到 `brew` 官网, http://brew.sh/,按指引安装，最重要的一步是，如下下载安装脚本：

```
ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

当执行脚本时，可能有目前权限问题。可以百度搜搜下如何解决 `/usr/local`目前权限问题。

### 第二步: 执行 `brew` 命令安装`hugo`

如果你想使用最新不稳定的开发版本，可以将命令`brew install hugo` 替换成 `brew install hugo --HEAD` ，可能存在很多Bug！

```
$ brew install hugo
==> Downloading https://homebrew.bintray.com/bottles/hugo-0.13_1.yosemite.bottle.tar.gz
######################################################################## 100.0%
==> Pouring hugo-0.13_1.yosemite.bottle.tar.gz
🍺  /usr/local/Cellar/hugo/0.13_1: 4 files,  14M
```

`Brew` 会更新Hugo到指定目录，打开 terminal 窗口执行脚本,确认安装位置：

```
$ # show the location of the hugo executable
$ which hugo
/usr/local/bin/hugo

$ # show the installed version
$ ls -l $( which hugo )
lrwxr-xr-x  1 mdhender admin  30 Mar 28 22:19 /usr/local/bin/hugo -> ../Cellar/hugo/0.13_1/bin/hugo

$ # verify that hugo runs correctly
$ hugo version
Hugo Static Site Generator v0.13 BuildDate: 2015-03-09T21:34:47-05:00
```

### 第三步: 完成

安装完Hugo,现在你可以使用Hugo创建网站，见
[快速入门指引](/overview/quickstart/), 阅读文档,如果还有疑问，尽管来
[讨论!](http://discuss.gohugo.io/ "Discussion forum")

## 安装包安装

### 第一步: 选择安装位置

当从安装包安装Hugo时，你必须选择将安装包安装到 `/usr/local/bin` 目录下，或者你的Home目录下. 有三个位置供选择。

1. 安装到 `/usr/local/bin`,所有用户都可以访问使用，这是比较好的选择，基本最常见的安装位置。缺点是你可能需要提升权限将安装包安装到此目录，对于多用户系统来说，将使用相同的Hugo版本，也许是个问题。 

2. 安装到  `~/bin`,这样只有你能够使用。这也是好的选择，安装非常容易，不需要提升权限。缺点是，只用你能够使用Hugo，如果其他用户想使用，必须存放到各自的目录下，可以让不同用户运行不同版本。当然你可以让你轻松尝试不同Hugo版本，而不影响其他用户。

3. 安装到网站工作目录下,对于你只需要创建一个网站来说，这是可选用的方案。确保任何内容之在一个地方，如果你想尝试新版本，只需要复制覆盖到该目录即可。

三种选择供你选择，我喜欢第二种方案。

### 第二步: 下载安装包

1. 浏览器打开 <https://github.com/spf13/hugo/releases> 页面。

2. 滚动页面，找到最新版本绿色标签位置 "Latest Release."

3. 下载适合Mac电脑的最新版本。安装包名称类似于 `hugo_X.YY_darwin_amd64.zip`, 这里的  `X.YY` 表示安装包版本序号。

4. By default, the tarball will be saved to your `~/Downloads` directory. If you chose to use a different location, you'll need to change that in the following steps.

### 第三步: 下载确认

验证安装包下载是否完整:

```
$ tar tvf ~/Downloads/hugo_0.13_darwin_amd64.zip
-rwxrwxrwx  0 0      0           0 Feb 22 04:02 hugo_0.13_darwin_amd64/hugo_0.13_darwin_amd64
-rwxrwxrwx  0 0      0           0 Feb 22 03:24 hugo_0.13_darwin_amd64/README.md
-rwxrwxrwx  0 0      0           0 Jan 30 18:48 hugo_0.13_darwin_amd64/LICENSE.md
```

 `.md` 文件是帮助文档，其他文件是执行文件。

### 第四步: 安装到Bin目录

```
$ # 如果没有，则创建目录
$ mkdir -p ~/bin

$ # 进入目录
$ cd ~/bin

$ # 解压安装包
$ unzip ~/Downloads/hugo_0.13_darwin_amd64.zip
Archive:  hugo_0.13_darwin_amd64.zip
  inflating: hugo_0.13_darwin_amd64/hugo_0.13_darwin_amd64
  inflating: hugo_0.13_darwin_amd64/README.md
  inflating: hugo_0.13_darwin_amd64/LICENSE.md

$ ls -l
total 7704
lrwxr-xr-x  1 mdhender  staff       22 Sep 29 13:34 hugo -> hugo_0.12_darwin_amd/hugo_0.12_darwin_amd64
drwxr-xr-x@ 1 mdhender  staff      102 Sep  1 14:17 hugo_0.12_darwin_amd64
drwxrwxr-x@ 5 mdhender  staff      170 Mar 28 22:46 hugo_0.13_darwin_amd64
-rw-r-----@ 1 mdhender  staff  3942651 Mar 28 22:45 hugo_0.13_darwin_amd64.zip

$ ls -l hugo_0.13_darwin_amd64
total 27560
-rw-r--r--@ 1 mdhender  staff      2707 Jan 30 18:48 LICENSE.md
-rw-r--r--@ 1 mdhender  staff      6748 Feb 22 03:24 README.md
-rwxr-xr-x@ 1 mdhender  staff  14095060 Feb 22 04:02 hugo_0.13_darwin_amd64
```

我已经在使用Hugo 0.12版本，下面操作后，将变成是v0.13版本。

```
$ # 创建文件映射
$ rm -f hugo
$ ln -s hugo_0.13_darwin_amd64/hugo_0.13_darwin_amd64 hugo
$ ls -l
total 7704
lrwxr-xr-x  1 mdhender  staff       22 Mar 28 22:49 hugo -> hugo_0.13_darwin_amd/hugo_0.12_darwin_amd64
drwxr-xr-x@ 1 mdhender  staff      102 Sep  1 14:17 hugo_0.12_darwin_amd64
drwxrwxr-x@ 5 mdhender  staff      170 Mar 28 22:46 hugo_0.13_darwin_amd64

$ # 运行验证
$ ./hugo version
Hugo Static Site Generator v0.13 BuildDate: 2015-02-22T04:02:30-06:00
```

你需要将bin目录添加环境变量 `PATH` 中.  用`which` 命令检查路径 . 如果它能找到 `hugo`, 将输出完整的Hugo路径,否则不会显示任何内容。

```
$ # 检查Hugo是否在PATH中
$ which hugo
/Users/mdhender/bin/hugo
```

如果 `hugo` 不在环境变量`PATH`中,需要添加到 `~/.bash_profile` 文件中. 首先,打开编辑器：

```
$ nano ~/.bash_profile
```

新增一行，添加到 `PATH` 环境变量中:

```
export PATH=$PATH:$HOME/bin
```

再按下 Control-X, 退出，按  `Y` 保存文件退出编辑。

退出后，还需要重新加载文件，让修改内容生效：
```
$ source ~/.bash_profile
```

你也可以使用你自己喜欢的编辑器，编辑该文件。再次运行 `which hugo` 命令进行检查。

### 第五步: 完成

你安装完Hugo,现在你可以使用Hugo创建网站，见
[快速入门指引](/overview/quickstart/), 阅读文档,如果还有疑问，尽管来
[讨论!](http://discuss.gohugo.io/ "Discussion forum")

## 从源码安装

如果你想自己编译安装Hugo，你需要使用
[Go](http://golang.org), 可以通过`brew
install go`安装。

### 第一步：获取源码

如果你需要特定版本源代码，去 
<https://github.com/spf13/hugo/releases>  选择你所需要的版本源代码 。如果你需要最新版本，直接Clone到本地：

```
git clone https://github.com/spf13/hugo
```

### 第二步：编译

新建包括源码的文件夹，并建立映射关系：

```
mkdir -p src/github.com/spf13
ln -sf $(pwd) src/github.com/spf13/hugo

# 第四步：设置Go工作目录
export GOPATH=$(pwd)

go get
```

上面命令将更新与该Hugo版本所依赖的包，因此如果Hugo编译失败，可能是依赖的包已被修改。

进行编译：

```
go build -o hugo main.go
```

然后将  `hugo` 执行文件连接，添加到环境变量 `$PATH` 中。

### 第三步：完成

安装结束完成，开始去做动手创建网站吧！
