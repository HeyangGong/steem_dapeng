---
title: "Build a mirror/backup site for your own steem posts in 30 minutes - 30 分钟搭建自己的 steem 镜像备份网站"
author: dapeng
date: "2017-11-06 09:44:42"
slug: build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem
categories: [steemdev]
tags: 
  - steemdev
  - steemit
  - cn
  - programming
  - steemsql
---

原文链接: [steemit](https://steemit.com/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [cnsteem](https://cnsteem.com/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [busy](https://busy.org/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [chainbb](https://chainbb.com/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [steemdb](https://steemdb.com/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [steemd](https://steemd.com/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [busy](https://busy.org/steemdev/@dapeng/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem), [markdown](https://raw.githubusercontent.com/pzhaonet/steem_dapeng/master/content/post/build-a-mirror-backup-site-for-your-own-steem-posts-in-30-minutes-or-30-steem.md)

Yesterday, I built two mirror sites for my steem posts ([mirror 1](https://dapeng.netlify.com/)，[mirror 2](https://steemit.netlify.com/)) as backups, which are synced automatically everyday, thanks to steemsql and steemdata. The mirror sites are very useful:

1. for emergency, in case that steemit.com and busy.org are down,
2. as backups, in case that steemsql and steemdata are gone,
3. for revision, where the posts are allowed to be modified even after 7 days,
4. for more replies, thanks to disqus, 
5. for a stable looking, no matter how the interface of steemit changes in the future, and
6. for fast browsing, especially when your posts are more than 100.

Both of these sites are free of costs, and updated automatically. 

How long does it take to build a site like them?

Following my steps, it takes less than half an hour, if you are an expert on R language. For newbies, it depends on how long it takes you to learn R. Anyway, you will save much time that I wasted in many failed attempts.

![mirror1.jpg](https://steemitimages.com/DQmVGn1eWfueYNVC9Xw4Hy41F9xDPR16jdGojPCDcJsfVxv/mirror1.jpg)

Here are the steps.

### Build a Hugo site with R blogdown

1. Install R and RStudio.
2. Created a blogdown project from RStudio's menu.

### Download your posts from steemsql or steemdata

1. R RODBC can visit steemsql database, and R mongolite can visit steemdata database. Either is OK.
2. Download the target posts, and organize them into markdown files with R.
3. Copy the markdown files into the contents folder in your site folder.
4. Run the build_site() function in R blogdown.

### Publish your site folder to Github

Create a new repo on Github, and publish your site folder.

### Deploy with Netlify

1. Log in Netlify.com with your github account. 
2. Created a new site, choose your site folder from github, and use hugo_0.19 as the command.
3. Wait seconds or minutes, and you can visit your mirror sites!

### Sync automatically everyday

1. Write a .bat script on Windows, or .sh script on Linux, to call your R script, which downloads the new posts, builds the site, and syncs with Github repo.
2. Use the task scheduler on Windows or crontab on Linux to run the .bat or .sh automatically everyday or every hour or whatever.

That's all. Wish you success!


![mirror2.jpg](https://steemitimages.com/DQmbNZ7kw2ynuig2qZjhmDPHKynQobL2iiSatQsGJgQJZiB/mirror2.jpg)

昨天，我为自己在 steem 上发布的帖子制作了两个镜像网站（[镜像1](https://dapeng.netlify.com/)，[镜像2](https://steemit.netlify.com/)）。每天定时跟 steem 同步更新，作为备份用。



镜像网站的好处是：

1. 应急。万一 steemit.com、busy.org 等前端网站挂了，至少我自己的文章还能来镜像访问。
2. 备份。有朝一日万一 steemsql 等数据库黄了，万一区块链挂了，我辛辛苦苦码出的文章还健在。
3. 修改。steem 上的文章过了7天后就没法修改，而镜像网站的永远可以修改，可以精益求精。
4. 评论。镜像网站上配置的是 disqus 评论系统，多引入一个评论方式。
5. 美观。不管 steemit 等网站界面好看难看，我有一片独立的自留地。
6. 快捷。找自己的文章时，再也不用往下拉，载入，等待，再拉，再载入，再等待……

这两个镜像全部是免费搭建的，搭建完毕后就每天自动更新，不用再操心了。

那么，搭建一个这样的网站需要多久？

熟悉 R 语言的话，从零开始到成功访问，整个过程用不了半小时。如果是 R 语言的新手，那么主要取决于多久能学会 R。无论如何，我花了很多时间来尝试，才建立了下面的步骤，这个时间你可以省了。

搭建这两个网站，用的主要工具是 R 语言的 blogdown 包。大体流程是：用 R 语言在本地搭建一个 Hugo 框架的静态网站，然后同步到 GitHub，再由 Netlify 布署。

下面简要说说步骤。

### 用 R 语言搭建 Hugo 网站

1. 先安装 R 语言和 RStudio。
2. 从 RStudio 的菜单栏创建一个 blogdown 项目，选择中意的网站主题，用不了1分钟，一个静态的 HUGO 网站框架就搭建好了，所有文件都保存在本地的一个文件夹里。

### 用 R 语言从 steemsql 或 steemdata 下载帖子

1. 如果访问 steemsql 数据库，请安装 R 语言的 RODBC 包；如果访问 steemdata 数据库，请安装 mongolite 包。两个数据库都可以提供 steem 上文章的所有信息。
2. 从数据库将需要的帖子下载到本地，并整理成 markdown 格式的文本文件。
3. 将文本文件拷贝到你的网站文件夹的 contents 里。
4. 运行 R blogdown 的建站函数。

### 将网站文件夹发布到 Github

在 Github 上创建一个新的项目，将你的网站文件夹发布上去。

### 用 Netlify 布署

用你的 Github 账号登陆 Netlify，创建一个新站点，选择你的网站文件夹，并用 hugo_0.19 作为布署命令。设置完毕后，短则几秒，长则几分钟，就可以访问你的镜像网站啦！

Netlify 提供免费的二级域名。当然，你也可以买个域名来绑定。

### 每天自动同步

1. 编写一个批处理程序，来调用 R 代码，从而完成下载帖子、建站、与 GitHub 同步的工作。
2. 用 Windows 的自动任务，每天自动运行上述批处理，就实现了每天自动同步。

最近我在看美剧《西部世界》。我的机器人 @pzhao 可不能亏待，所以我为 @pzhao 也做了一个[镜像](https://pz.netlify.com/)。





![dapeng](https://steemitimages.com/DQmeYUwQ7Juorgd79o6D5E34BnUYxwfmLxYH4cApgPRhRf6/end2.jpg)
