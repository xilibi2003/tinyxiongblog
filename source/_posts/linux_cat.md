---
title: Linux常用命令系列 - echo命令
date: 2017-08-26 16:36:36
categories: 
    - Linux
    - 命令
tags: 
    - Linux
    - 命令
    - echo
author: Tiny熊
---

echo 是Linux 下最常用的命令之一，用于终端打印。

<!-- more -->
## 常用用法
```bash
$ echo "Hello Bash"    
Hello Bash
```

小技巧：

1. 使用转义字符
```bash
$ echo  -e "Hello\tBash"
Hello    Bash
```

2. 使用转义字符打印彩色输出，如红色打印
```bash
$ echo  -e "\e[1;31m Hello Bash \e[0m"
Hello Bash
```

\e[1;31m 表示将颜色设置为红色  

颜色编号： 30 (黑色)、31 (红色)、32 (绿色)、33 (黄色)、34 (蓝色)、35 ( 紫红色)、36 (青色)和37 (白色)

\e[0m 表示将颜色重新置回


如果要进行格式化打印可以使用printf， 如：
```bash
$ printf "%-10s %-10s %-4.2f\n" Hello Bash 88.8888
Hello      Bash       88.89
```

printf更多用户用法，有兴趣的可以[参考](https://www.computerhope.com/unix/uprintf.htm)。

## 使用截图：
![屏幕快照 2016-11-29 下午9.47.40.png](/images/linux_cat.png)

