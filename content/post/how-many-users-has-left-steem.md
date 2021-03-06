---
title: "Steemit 新人流失到底有多严重 How many users have left steem"
author: dapeng
date: "2017-09-26 20:53:12"
slug: how-many-users-has-left-steem
categories: [cn]
tags: 
  - cn
  - steemit
  - steemswatch
  - cn-reader
---

原文链接: [steemit](https://steemit.com/cn/@dapeng/how-many-users-has-left-steem), [cnsteem](https://cnsteem.com/cn/@dapeng/how-many-users-has-left-steem), [chainbb](https://chainbb.com/cn/@dapeng/how-many-users-has-left-steem), [busy](https://busy.org/cn/@dapeng/how-many-users-has-left-steem), [markdown](https://raw.githubusercontent.com/pzhaonet/steem_mirror/master/content/post/how-many-users-has-left-steem.md)

在[关于 steemit 推广构想](https://steemit.com/cn/@dapeng/first-product-then-marketing)的讨论里，很多朋友都谈到steemit 用户流失的问题。到底流失有多严重？直接说我的分析结果吧：cn 区每新来 100 个用户，最后会有 79 个离开，21个留下，恰好等于空气里的氧气含量百分比。高于全网的流失率（63 %）。


> 63% of Steemians have left steemit. In CN category, 79% have left. This post analyzed the loss in Steem users in history with R language. Improvement in the user interface of steemit.com is highly expected.


---


大家对用户流失的感受是这样的：


> - @incrediblesnow: 每天，我在中文圈里检阅滥用帖子时，我都会发现有好多的新来用户完全不受理睬，而且，他们的文笔也是相当优秀，可是，他们是 零收入。 对的，他们是零收入。 完全无人打睬。渐渐地，我就没有再看到他们。

> - @htliao:不知道大家有沒有向朋友介紹Steemit的經驗，我自問也向不少朋友介紹過Steemit，他們都嘗試寫過一些文章，但他們大多玩了一會兒後就放棄了。

> - @kenchung: 其實是有不少新人加入steemit的，只不過流失率都很高，其實這才是問題的重點。我早前介紹過數名朋友，現在通通走光了，

> - @tumutanzi: 大量的用户过来不是坏事，真正的用户会留下来，那些不相关的用户自然会走的。

> - @fundurian: 我觉得，就算有 2000 人来，能坚持１个星期的有几个？可能200人，能坚持１个月的又有几个？可能不到20人了


这些仅仅是直观感受。如果看数据，可以参考 @arcange 每天发布的活跃用户状态。不过，我们需要更进一步的分析，才能得到明确结论，来???答朋友私下问我的问题：到底 steemit 的用户流失有多严重？


用万能的 R 语言，我们来好好探讨一下这个问题。


---


## 全网情况


首先，我们先看看 steemit 上的账号总数。截至今天（2017-09-26），注册用户共有385351个。


很多账号注册后就没有任何动作了，也搞不清楚是真人还是机器人账号。我们假定必须发过至少一篇 blog 才算有效，那么有效账号是 126811 个，占账号总数的 33%。我看到这个数字的时候有些吃惊：只有三分之一的账号发过帖子。剩下那三分之二的账号，要么沉寂无言，要么只回复或只点赞，从未正式发帖。





如何界定哪些用户算是流失了呢？我们假定，如果某个用户发过至少一次文章（blog），并且最后一次发文距离今天超过了 1 个月，那么就认为这个用户离开了。这样算来，steemit 全网流失的用户总数为79524个，占注册 ID 总数的 21%，占全网有效 ID 的63%。


下图显示了每天新注册的用户数量（蓝色），和发布了最后一帖的用户数量（红色）。


![unnamed-chunk-3-1.png](https://steemitimages.com/DQmeBtbVLTUiMECrUCiCrbcpCGcQHb3VyvLaPeazD1gHsQR/unnamed-chunk-3-1.png)


小结：结合前面的数据，steemit 全网约 39 万注册账号，其中三分之一发过帖子；而发过帖子的账号里，有 63% 的用户流失了。



## CN 区情况


上文说的是全网的情况。下面，我们用类似的方法，看看 CN 区的情况。


到底哪些账号算是 CN 区的有效账号？我们假定，凡是使用了 CN 标签发布过至少一篇文章的账号，就算 CN 区的有效账号，那么，截至一个月前，这样的账号共有 2364 个。


这些踏足过 cn 区的账号里，有 1865 个 ID 在最近一个月没有发过文章。也就是说，cn 区有效账号里， 79% 的用户已经流失了。这是历史整体数据。


我们再看看每天的数据。下图红色表示每天有多少用户是最后一次在 cn 区发文章（简称“死亡”），蓝色点表示一天里有多少用户是第一次在 cn 区发文章（简称“新生”）。


![unnamed-chunk-5-1.png](https://steemitimages.com/DQmYBB43dz5h2WCuyrhzVQffhwZwxKE5vQHuZNhswNjgeXv/unnamed-chunk-5-1.png)


cn 区的新生用户占死亡用户的比例是多少，见下图。可以看出来，最惨烈的时候，是 2017 年 1 月的某一天，死亡用户是新生用户的四倍。而  2017 年 6 月以来，情况乐观多了，比例大约是 0.5。而那些等于 1 的日子里，死亡用户跟出生用户数量持平。有 1386 个用户，占 cn 区有效用户总数的 59%， 他们在 cn 区只发了一篇文章，就拂袖而去，再也没有回头。


![unnamed-chunk-6-1.png](https://steemitimages.com/DQmcvUh77aLXPCC6naJDaGEDy5ZxHf6K6ss7p2tezBpg5nM/unnamed-chunk-6-1.png)


## 结语


我在《[推广之前先做好产品：也谈 steemit 的推广构想](https://steemit.com/cn/@dapeng/first-product-then-marketing)》一文里讲到：


> 我没有向任何亲朋好友推荐 steemit，一个都没有。为什么？现在推荐的话，让有些人失望而去，即使将来 steemit 够好了，想再拉也拉不回来了。与其这样，我宁可强忍着如火的热情，等待时机成熟的那一天。


写上面这句话的时候，我并没有数据支持。现在有了数据，更坚定了我这个想法。我的朋友本来就不太多，如果每拉10个，最后只留下2个，那么我还是别拉了。


时机，尚未成熟。我期待着 steemit.com 能先把界面变得对新人友好一些，或者我们搭建我们自己的 steemit.cn，多留下几个新人。


对此，你怎么看？欢迎留言谈谈你的想法。


![end.png](https://steemitimages.com/DQmWKRoZhpvHW3sFkHUnfkbZGNsZUe8FBEgEbkRXQXoE4bu/end.png)
