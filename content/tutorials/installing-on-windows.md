---
author: "Michael Henderson"
date: 2015-03-30
linktitle:  Windows上安装
toc: true
menu:
  main:
    parent: tutorials
next: /tutorials/mathjax.html
prev: /tutorials/installing-on-mac.html
title: 在Window上安装Hugo
weight: 10
---

# 在Window上安装Hugo

本教程指导你如何在Windows电脑上一步一步完成Hugo安装。 

## 前提

1. 你需要知道如何在Window上执行命令。
2. 你需要64位电脑。
3. 你的网站 `example.com`。
4. 你使用 `D:\Hugo\Sites` 目录开始新建网站。
5. 你将使用 `D:\Hugo\bin` 来存储安装包。

## 设置目录

你需要一个目录来存放Hugo安装包、网站（用于创建网站），生产内容（网站生成的HTML内容）。 

1. 打开我的电脑目录。
2. 新建文件夹： `D:\Hugo`。
3. 新建文件夹： `D:\Hugo\bin`。
4. 新建文件夹： `D:\Hugo\Sites`。

## 下载Hugo的Window版安装包

Hugo安装包是绿色的，不需要你点击进行安装，双击即可执行。你只需要拷贝Hugo.exe文件到硬盘即可，我们现在可以拷贝到`D:\Hugo\bin`目录。

1. 浏览器打开 https://github.com/spf13/hugo/releases 页面。
2. 当前版本是 hugo_0.15_windows_amd64.zip。
3. 下载ZIP文件保存到 `D:\Hugo\bin` 目录。
4. 下载后，找到ZIP文件，解压到当前目录。
5. 解压后，你可以看到 `hugo_0.13_windows_amd64.exe` 文件。
6. 重命名为 `hugo.exe`。
7. 确保 `hugo.exe` 文件是直接在 `D:\Hugo\bin` 文件夹下面. (有可能在子目录下，如果是的话，直接拷贝到 `D:\Hugo\bin`即可。)。
8. 添加 hugo.exe 文件到环境变量PATH中，执行命令：
 {{< nohighlight >}}C:\Program Files> cd D:\Hugo\bin
C:\Program Files> D:
D:\Hugo\bin> set PATH=%PATH%;D:\Hugo\bin
{{< /nohighlight >}}

## 验证Hugo.exe

执行Hugo命令，验证Hugo是否可正常运行。

1. 打开命令窗口。

2. 在窗口中,输入`hugo help` 按下回车键,你应该可以看到下面内容：

    {{< nohighlight >}}A Fast and Flexible Static Site Generator built with love by spf13 and friends in Go. Complete documentation is available at http://gohugo.io
{{< /nohighlight >}}

    如果你能看到，这说明安装完成。如果你没看到，需要再检查下是否有将 `hugo.exe` 文件目录添加到环境变量PATH中。如果还是不行，你可以将问题反馈到Hugo[讨论组](https://discuss.gohugo.io/)，并发布到**Support**组，贴出你所执行的命令以及显示结果。

3. 在命令查看，切换到 `Sites` 文件夹.

    {{< nohighlight >}}C:\Program Files> cd D:\Hugo\Sites
C:\Program Files> D:
D:\Hugo\Sites>
{{< /nohighlight >}}

4. 运行命令创建网站，我使用`example.com` 作为网站名称。

    {{< nohighlight >}}D:\Hugo\Sites> hugo new site example.com
{{< /nohighlight >}}

5. 此时，出现个文件夹 `D:\Hugo\Sites\example.com`. 进入该文件夹，列出文件信息，你可以看到如下内容： 

    {{< nohighlight >}}D:\Hugo\Sites&gt;cd example.com
D:\Hugo\Sites\example.com&gt;dir
&nbsp;Directory of D:\hugo\sites\example.com
&nbsp;
04/13/2015  10:44 PM    &lt;DIR&gt;          .
04/13/2015  10:44 PM    &lt;DIR&gt;          ..
04/13/2015  10:44 PM    &lt;DIR&gt;          archetypes
04/13/2015  10:44 PM                83 config.toml
04/13/2015  10:44 PM    &lt;DIR&gt;          content
04/13/2015  10:44 PM    &lt;DIR&gt;          data
04/13/2015  10:44 PM    &lt;DIR&gt;          layouts
04/13/2015  10:44 PM    &lt;DIR&gt;          static
               1 File(s)             83 bytes
               7 Dir(s)   6,273,331,200 bytes free
{{< /nohighlight >}}

现在，你已完成Hugo安装和新建网站工作目录，你可以添加布局或者主题文件，开始新建文章丰富网站，可参见[Hugo快速入门]({{<relref "overview/quickstart.md">}}) 手册。

## 故障处理

@dhersam 提供一个常见文件解决视频： https://www.youtube.com/watch?v=c8fJIRNChmU