---
authors:
- Arjen Schwarz
- Samuel Debruyn
date: 2015-01-12
linktitle: 自动部署
toc: true
menu:
  main:
    parent: tutorials
next: /tutorials/creating-a-new-theme.html
prev: /community/contributing.html
title: 使用Wercker自动部署网站
weight: 10
---

# 使用Wercker自动部署网站

本篇教程我们将使用免费工具Wercker通过简单配置实现新增文章自动部署。本教程将非常轻松的部署网站到Github中，将一步一步教你部署，还有截图。 

开始前你需要知道如何使用版本控制工具Git,还需要一个Github账号。如果没有，你可以看Github的[帮助文档]((https://help.github.com/articles/set-up-git/))，将你如何快速使用Git和轻松注册免费的Github账户。

## 新建Hugo网站

在配置运行网站之前，你需要参考 [快速入门手册]({{< relref "overview/quickstart.md">}}) 文档。它指导你一步一步安装配置Hugo，全部操作基于命令，还是挺方便的。 

使用命令`hugo new site`新建网站，再进入目录。
```bash
hugo new site hugo-wercker-example
cd hugo-wercker-example
```

使用命令克隆一份主题到主题包目录下。
```bash
mkdir themes
cd themes
git clone https://github.com/spf13/herring-cove.git
```
克隆的主题会影响我们自己的版本控制，因此删除克隆主题下的git配置。
```bash
rm -rf herring-cove/.git
```
 
快速添加**about**页面

```bash
hugo new about.md
```

现在，我们可以编辑内容contents/about.md ,添加些文字，同时设置为非草稿。 

```bash
hugo undraft content/about.md
```

完成后，一种便捷方式快速检查网站是否工作正常。

```bash
hugo server --theme=herring-cove
```
如果一切正常，你可以在浏览器打开*localhost:1313*，你应该可以看到和下面截图一样的信息。

![][1]

[1]: /img/tutorials/creating-a-basic-hugo-site.png

## 设置版本控制

在网站根目录下执行命令 `git init` 将我们的网站项目纳入版本管理中。 

```bash
git init
```

执行命令 `git status` 被版本管理的内容有： **config.toml**文件 ,**themes**文件夹, **contents** 文件夹,以及 **public** 文件。但是我们不需要将 **public** 文件进行版本控制，这个目录最终是使用wercker自动生成的。需要通过命令将文件夹排除在git版本控制之外。

```bash
echo "/public" >> .gitignore
```

现在我们没有添加主题之外的任何静态文件，Wercker能够在编译网站时自动将主题合并到网站下。现在，我们可以添加些静态文件到static文件夹。比如添加个robots.txt静态文件，让所有搜索引擎都可以访问。 

```bash
echo "User-agent: *\nDisallow:" > static/robots.txt
```

现在我们可以将所有内容添加到版本库中。 

```bash
git commit -a -m "Initial commit"
```

## 上传项目到Github

首先，我们需要到Github新建项目库(repository)。点击右上方的 **+**按钮，进入 https://github.com/new 页面。


输入项目库名称 (**hugo-wercker-example**)，检查通过后，保存项目。将刚在Github新增的项目和本地项目建立关系，并推送本地项目到Github。

```bash
git remote add origin git@github.com:YourUsername/hugo-wercker-example.git
git push -u origin master
```

![][2]

[2]: /img/tutorials/adding-the-project-to-github.png

## 欢迎使用wercker

开始前，需要注册wercker账户。进入http://wercker.com 页面，点击 **Sign up** 按钮注册.

![][3]

[3]: /img/tutorials/wercker-sign-up.png

## 注册

为了简单方便，直接使用Github注册，如果不想使用Github注册，你就输入用户名，邮箱，密码进行注册。 

![][4]

[4]: /img/tutorials/wercker-sign-up-page.png

## 连接到 GitHub/Bitbucket

注册后，需要将Github/Bitucket关联到Wercker，在个人设置页面，点击  "Git connections" 进行关联。如果你是通过Github注册的则默认会自动关联(如下图)。点击" connect "关联授权。如果后续出现关联授权失败，需要重新登录Github或者Bitucker授权Wercker关联。 
![][5]

[5]: /img/tutorials/wercker-git-connections.png

## 新建项目

现在已做好前期准备工作，现在需要对项目进行配置即可，先点击**+ Create**按钮，再选择Github选项。

![][6]

[6]: /img/tutorials/wercker-add-app.png

## 选择项目库

选择Github后，Wercker后罗列出你在Github上的项目库。如果项目太多，你也可以输入名称进行筛选。选中前面所创建的**hugo-wercker-example**项目库（不一定是这个，要看你前面创建的是哪个项目库），再点击"Use selected repo"。

![][7]

[7]: /img/tutorials/wercker-select-repository.png

## 选择项目库所有者

这一步，Wercker会要你选择这个项目库的所有者。你只需选择你的Github账户即可，并继续。

![][8]

[8]: /img/tutorials/wercker-select-owner.png

## 配置权限

这步比较棘手，默认情况下Wercker没法访问迁出你的私有项目，Wercker所有需要跟你确定访问方式。当你的项目是公开的，如使用GitHub Pages创建网站，则任何人都可以在Github上访问查看项目。

![][9]

[9]: /img/tutorials/wercker-access.png

## Wercker.yml

Wercker 会尝试为你初始化一个 *wercker.yml*文件，文件用于配置项目和Wercker的关联信息。因我们刚新建的项目没有特殊之处，可以直接**Copy  to clipborad**复制文件内容到新建 *wercker.yml*文件下。文件新建在到项目根目录下。后续配置些信息让其自动做些事情。 

![][10]

[10]: /img/tutorials/werckeryml.png

## 是否公开

这是可选的。一个公共的App是而任何人都可以看到它的细节信息。公开没有任何实际的好处，但作为教材的一部分，故公开了APP，因此你可以看到它的情况,[点击查看APP](https://app.wercker.com/#applications/5586dcbdaf7de9c51b02b0d5).

![][11]

[11]: /img/tutorials/public-or-not.png

## 获得App

现在已创建了App，Wercker会监控变化进行构建。现在我们还没有提交 **wercker.yml**文件到Github，故不会触发。 

![][12]

[12]: /img/tutorials/and-we-ve-got-an-app.png

## 添加步骤

现在需要添加执行步骤。首先点击页面左上方 "Registry"按钮，搜索  "hugo build",点击选择结果中第一个Task  **Hugo-Build** .
![][13]

[13]: /img/tutorials/wercker-search.png

## 使用 Hugo-Build

点击进入详情页，有介绍如何使用。上面部分是一些基本用法说明，滚动到下面是README内容，是一个详细且完整的使用说明。

本教材，我们还不需要使用任何高级功能。返回我的项目，将下面内容添加到** wercker.yml **文件中。在commit前可以有效的使用Wercker提供的一个[工具](http://devcenter.wercker.com/articles/werckeryml/validate.html)来验证配置文件 wercker.yml 的正确性。

```yaml
box: debian
build:
  steps:
    - arjen/hugo-build:
        version: "0.14"
        theme: herring-cove
        flags: --buildDrafts=true
```

这就完成了第一步，我们可以测试下，在commit **wercker.yml**文件后，将发生些神奇的事情。 

```bash
git commit -a -m "Add wercker.yml"
git push origin master
```

 一旦完成，你可以在你的第一个版本的前面看到一个漂亮的勾，你可以点击它查看详细信息。但是，现在我们还需要将网站部署到GitHub Pages上。 

![][14]

[14]: /img/tutorials/using-hugo-build.png

## 添加 GitHub Pages 操作

在部署到GitHub Pages之前，需要添加一个部署执行步骤。再一次进入*repository*，输入搜索**lukevevier/gh-pages** 。lukevevier/gh-pages**需要添加配置信息到  wercker.yml 文件。执行部署操作前需要确保 box 中安装git和ssh，可以通过添加命令进行配置，具体如下： 

```yaml
box: debian
build:
  steps:
    - arjen/hugo-build:
        version: "0.14"
        theme: herring-cove
        flags: --buildDrafts=true
deploy:
  steps:
    - install-packages:
        packages: git ssh-client
    - lukevivier/gh-pages@0.2.1:
        token: $GIT_TOKEN
        domain: hugo-wercker.ig.nore.me
        basedir: public
```

如何让上面的配置生效？ 需要做几件事情，首先需要一个域名，配置好让GitHub Pages总能指向你的域名。第二点需要配置一个**public** 基础目录，这个目录专门用于存放网站内容。最后，你看上面的变量 **$GIT_TOKEN**,它用于推送修改内容到GitHub所需要的令牌。这个需要在Wercker中配置，打开App配置页面，点击**Deploy targets**新增一个**Add deploy target**,选择 **Custom deploy**。

![][15]

[15]: /img/tutorials/adding-a-github-pages-step.png

## 配置部署

简单输入名称，启用从**master**分支自动部署。添加一个名为 **GIT_TOKEN**的变量，用于访问Github的令牌。 参考 [GitHub帮助文档](https://help.github.com/articles/creating-an-access-token-for-command-line-use/)生成一个访问令牌。 这样，在Wercker的部署配置以完成。更新推送wercker.yml 文件到Github，Wercker将自动创建一个Gitub Pages 网站。本教程可以访问 http://hugo-wercker.ig.nore.me 。

![][16]

[16]: /img/tutorials/configure-the-deploy-step.png

## 总结

现在，任何时候你需要发布一篇博文到网站，只需要提交上传博文内容到GitHub，其他就会自动完成。 当前教程示例源代码在[GitHub](https://github.com/ArjenSchwarz/hugo-wercker-example)上，基于  [Hugo Build step](https://github.com/ArjenSchwarz/wercker-step-hugo-build) 自动编译.

如果你想知道如何部署到S3，可参见 [Wercker 帮助文档](http://devcenter.wercker.com/docs/deploy/s3.html) 进行配置。
