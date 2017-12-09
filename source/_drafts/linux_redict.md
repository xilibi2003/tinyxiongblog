 

 
 1重定向

1.1      重定向符号

>               输出重定向到一个文件或设备 覆盖原来的文件
>!              输出重定向到一个文件或设备 强制覆盖原来的文件
>>             输出重定向到一个文件或设备 追加原来的文件
<               输入重定向到一个程序 

1.2标准错误重定向符号

2>             将一个标准错误输出重定向到一个文件或设备 覆盖原来的文件  b-shell
2>>           将一个标准错误输出重定向到一个文件或设备 追加到原来的文件
2>&1         将一个标准错误输出重定向到标准输出 注释:1 可能就是代表 标准输出
>&             将一个标准错误输出重定向到一个文件或设备 覆盖原来的文件  c-shell
|&              将一个标准错误 管道 输送 到另一个命令作为输入

1.3命令重导向示例

在 bash 命令执行的过程中，主要有三种输出入的状况，分别是：
1. 标准输入；代码为 0 ；或称为 stdin ；使用的方式为 <
2. 标准输出：代码为 1 ；或称为 stdout；使用的方式为 1>
3. 错误输出：代码为 2 ；或称为 stderr；使用的方式为 2>

[test @test test]# ls -al > list.txt
将显示的结果输出到 list.txt 文件中，若该文件以存在则予以取代！

[test @test test]# ls -al >> list.txt
将显示的结果累加到 list.txt 文件中，该文件为累加的，旧数据保留！

[test @test test]# ls -al  1> list.txt   2> list.err
将显示的数据，正确的输出到 list.txt 错误的数据输出到 list.err

[test @test test]# ls -al 1> list.txt 2> &1
将显示的数据，不论正确或错误均输出到 list.txt 当中！错误与正确文件输出到同一个文件中，则必须以上面的方法来写！不能写成其它格式！
[test @test test]# ls -al 1> list.txt 2> /dev/null
将显示的数据，正确的输出到 list.txt 错误的数据则予以丢弃！ /dev/null ，可以说成是黑洞装置。为空，即不保存。

1.4为何要使用命令输出重导向

• 当屏幕输出的信息很重要，而且我们需要将他存下来的时候；
• 背景执行中的程序，不希望他干扰屏幕正常的输出结果时；
• 一些系统的例行命令（例如写在 /etc/crontab 中的文件）的执行结果，希望他可以存下来时；
• 一些执行命令，我们已经知道他可能的错误讯息，所以想以『 2> /dev/null 』将他丢掉时；
• 错误讯息与正确讯息需要分别输出时。

2   管线命令 ( pipe )

就如同前面所说的， bash 命令执行的时候有输出的数据会出现，那么如果这群数据必需要经过几道手续之后才能得到我们所想要的格式，应该如何来设定？这就牵涉到管线命令的问题了（ pipe ），管线命令使用的是『 | 』。

例子：简单的管线命令
假设我们要读取 last 这个指令中，那个 root 登入的『次数』应该怎么作？
那么我所进行的步骤是：
1. 执行 last ，将所有这个月的所有人登入数据取出来；
2. 使用 grep 将上面的输出数据（stdout）当中的 root 撷取出来，其它的不要；
3. 使用 wc 这个可以计算行数的指令将上一步的数据计算行数！
由于 last 的输出是一行代表一次登入，所以只要计算几行就代表登入几次的意思，经由上面三个步骤，将 last 数据逐步的筛选，就可以得到我们的数据了！整个命令可以写成如下： [test @test bin]# last | grep root | wc -l
这个管线命令『 | 』仅能处理经由前面一个指令传来的正确信息，也就是standard output ( STDOUT ) 的信息，对于 stdandard error 并没有直接处理的能力。

2.1基本的管线命令指令介绍

• cut
语法：[root @test /root ]# cut -d "分隔字符" [-cf] fields
参数说明：
-d ：后面接的是用来分隔的字符，预设是『空格符』
-c ：后面接的是『第几个字符』
-f ：后面接的是第几个区块？
范例：[root @test /root]# cat /etc/passwd | cut -d ":" -f 1
将 passwd 这个文件里面，每一行里头的 : 用来作为分隔号，而列出第一个区块！也就是姓名所在啦！
[root @test /root]# last | cut -c1-20
将 last 之后的数据，每一行的 1-20 个字符取出来！
• sort
语法：[root @test /root ]# sort [-t 分隔符] [(+起始)(-结束)] [-nru]
参数说明：
-t 分隔符：使用分隔符来隔开不同区间，预设是 tab
+start -end：由第 start 区间排序到 end 区间
-n ：使用『纯数字』排序（否则就会以文字型态来排序）
-r ：反向排序
-u ：相同出现的一行，只列出一次！
范例：[root @test /root]# cat /etc/passwd | sort将列出来的个人账号排序！
[root @test /root]# cat /etc/passwd | sort -t: +2n将个人账号中，以使用者 ID 来排序（以 : 来分隔，第三个为 ID ，但第一个代号为 0 之故）
[root @test /root]# cat /etc/passwd | sort -t: +2nr反相排序啰！
• wc
语法：[root @test /root ]# wc [-lmw]
参数说明：
-l ：多少行
-m ：多少字符
-w ：多少字
范例：[root @test /root]# cat /etc/passwd | wc -l这个文件里头有多少行？
[root @test /root]# cat /etc/passwd | wc -w这个文件里头有多少字！？
• uniq这个指令用来将『重复的行删除掉只显示一个』
语法：[root @test /root ]# uniq
范例：[root @test /root]# last | cut -d" " -f1 | sort | uniq
• tee命令重定向到文件的同时将数据显示在屏幕上
语法：[root @test /root ]# last | tee last.list | cut -d " " -f1
范例：[root @test /root]# last | tee last.list | cut -d " " -f1
• tr
语法：[root @test /root ]# tr [-ds] SET1
参数说明：
-d ：删除 SET1 这个字符串  
-s ：取代掉重复的字符！
范例：[root @test /root]# last | tr '[a-z]' '[A-Z]' <==将小写改成大写
[root @test /root]# cat /etc/passwd | tr -d : <== : 这个符号在 /etc/passwd 中不见了！
[root @test /root]# cat /home/test/dostxt | tr -d '\r' > dostxt-noM
• split
语法：[root @test /root ]# split [-bl] 输入文件 输出文件前导字符
参数说明：
-b ：以文件 size 来分
-l ：以行数来分
范例：[root @test /root]# split -l 5 /etc/passwd test <==会产生 testaa, testab, testac... 等等的文件
说明：在 Linux 底下就简单的多了！你要将文件分割的话，那么就使用 -b size 来将一个分割的文件限制其大小，如果是行数的话，那么就使用 -l line 来分割！
管线命令在 bash 的连续的处理程序中是相当重要的！另外，在 log file 的分析当中也是相当重要的一环。
管道输送到一个命令的标准输入可以使用标准输入参数”-“ 进行更仔细的控制.如cat命令的示例
eg:  sort mylist | more
sort mylist | cat –n | lpr
pwd | cat – mylist | lpr



https://mp.weixin.qq.com/s?__biz=MzIxNDMyODgyMA==&mid=2247483679&idx=1&sn=f98b8ef107264b9258f8ab76986b8f57&scene=0%23wechat_redirect