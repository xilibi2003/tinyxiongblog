---
title: Linux常用命令系列 - ls
date: 2017-08-26 16:36:36
categories: 
    - Linux
    - 命令
tags: 
    - Linux
    - 命令
author: Tiny熊
---

ls 是Linux 下最常用的命令之一，用于列出文件和目录。

<!-- more -->
## 常用用法
常用参数  -l(l : list) ： 显示文件（夹）内容详情 每行是一个文件的详情
```bash
> ls -l
drwxr-xr-x  6 Emmett  staff  204  9  4 17:18 man
-rw-r--r--  1 Emmett  staff    0 12  4 22:52 test_lastest
lrwxr-xr-x  1 Emmett  staff   13 12  4 22:58 p_readme -> ../readme.txt
```

每个文件的详情分别用7列来表示
第1列  第一个字母 表示文件类型  d 表示目录  - 表示文件 l 表示链接
剩下的9个字母表示文件权限， 以三个字母为一组（rwx），分别表示 拥有者 所有组 其他人的权限
第2列 表示多少链接指向这个文件
第3列  表示文件/文件夹的所有者
第4列 表示文件/文件夹的所有组
第5列 表示文件/文件夹大小，以字节为单位
第6列 表示文件最后的修改时间
第7列 表示文件名或目录名

常用参数 -lh (h : human) 易于人类阅读的文件大小:
```
> ls -lh
-rw-r--r--@ 1 Emmett  staff   960M 12  4 23:13 G718CH.zip
```

常用参数 -a (a: all) 显示所有文件（用于显示隐藏文件）
参数：-S (S : Size )以文件大小排序
参数： -t （t: time） 修改时间排序，新的文件在前
参数：-r (r: reverse) 反转顺序

## 组合用法
想一想， 如何查看最大的5个文件？
```
ls -S | head -5
```

## 事例截图
![](/images/linux_ls.png)

