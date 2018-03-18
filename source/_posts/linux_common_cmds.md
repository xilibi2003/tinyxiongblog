---
title: Linux常用命令列表 - 速查手册
date: 2017-08-01 16:36:36
categories: 
    - Linux
    - 命令
tags: 
    - Linux
    - 命令
    - 速查手册
author: Tiny熊
---

本文整理了Linux最常用一些命令，方便大家速查

<!-- more -->
## 常用命令
|命令|说明|
|:-----|:-----|| 
|**ls**      | 列出目录|
|**ls -al**      | 使用格式化列出隐藏文件| 
|**cd dir**      | 进入目录dir| 
|**cd**          | 进入 home 目录| 
|**pwd**         | 显示当前目录| 
|**mkdir dir**   | 创建目录 dir| 
|**rm file**     | 删除文件 file| 
|**rm -r dir**   | 删除目录 dir| 
|**rm -f file**  | 强制删除 file| 
|**rm -rf dir**  | 强制删除目录 dir | 
|**cp file1 file2**  | 将 file1 复制到 file2| 
|**cp -r dir1 dir2** | 将 dir1 复制到 dir2; 如果 dir2 不存在则创建它| 
|**mv file1 file2**  | 将 file1 重命名或移动到 file2; 如果file2 是已存在目录则将 file1 移动到目录 file2 中| 
|**ln -s file link** | 创建 file 的符号连接 link| 
|**touch file**  | 创建名file的文件| 
|**cat > file**  | 将标准输入添加到 file| 
|**more file**   | 查看 file 的内容| 
|**tail -f file**   | 从后 10 行开始查看 file 的内容| 
|**man command**  | 显示 command 的说明手册| 
|**ps**      | 显示当前的活动进程| 
|**top**     | 显示所有正在运行的进程| 
|**kill pid**        | 杀掉进程 id pid| 
|**killall proc**    | 杀掉所有名为 proc 的进程| 
|**chmod octal file** | 更改 file 的权限|
|**grep pattern files**  | 搜索 files 中匹配 pattern 的内容| 
|**df** | 显示磁盘占用情况| 
|**du** | 显示目录空间占用情况| 
|**tar xzf file.tar.gz** | 使用 Gzip 解压 tar 文件| 
|**tar xjf file.tar.bz2** | 使用 Bzip2 解压 tar 文件| 
|**ping host** | ping host 并输出结果| 
|**wget file** | 下载 file| 



[原始链接](http://tinyxiong.com/linux_common_cmds/):http://tinyxiong.com/linux_common_cmds/
关于作者：Tiny熊：[深入浅出区块链](https://learnblockchain.cn)博主
