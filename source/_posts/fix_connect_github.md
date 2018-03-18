---
title: 一招解决无法连接github问题
date: 2017-08-26 16:36:36
categories: 
    - Linux
    - github
tags: 
    - Linux
    - ssh
author: Tiny熊
---

因为大家都知道的原因，有时github没法连接上，本文给大家一个解决办法。

<!-- more -->
估计今天很多同学遇到了阿里云无法连github的问题。
想必遇到这个问题的你一定很恼火，过来看看吧，本文很短，但很实用。
## 前提
备一台香港服务器（可访问github的服务器都行）

## 设置Socks 代理
```
$ ssh -D 1080  hk_ip
```
这条命令在无法连接github的主机上执行。hk_ip 为hk服务器ip

## 给github 配置代理
在无法连接github的主机上，打开.ssh/config, 添加一下记录
```
Host github.com
  ProxyCommand=nc -X 5 -x localhost:1080 %h %p
  ```
  好了， 执行下git pull 试试看，已经可以成功访问github了。
