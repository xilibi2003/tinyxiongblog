---
title: 学习跨链
date: 2019-03-22 23:00:10
categories: 学习
tags:
    - 侧链
    - 侧链
author: Tiny熊
---


## 利用中介 跨链

如何把你手里 的1 BTC 换成 25 ETH， 对于你来说就是把 比特币的资产转移到了 以太坊，最简单直接的方法就是 找一个**中介**，他收到了  1 BTC 之后转给你 25 ETH，这就完成了跨链。

哈哈，简单粗暴，很熟悉吧，交易所就是干这个事，缺点很明显，就是中心化。

这种方式有一个词，叫： 公证人机制（Notary schemes）或见证人机制，是不是一下子高大上了。

其实 Ripple 就是用类似这种方式来跨链的。


## 哈希时间锁定（Hash-locking）

 利用中介很容易发生一个问题， 中介收到我们的BTC后就跑路了， 不给我们打ETH。
 
哈希时间锁定（HTLC）最早出现在比特币的闪电网络，支持跨链资产进行**原子**交换。

它用到了两把锁：哈希锁和时间锁。迫使资产的接收方在期限内确定收款并产生一种收款证明给付款方，否则资产会归还给付款方。

用一个例子来阐述如何使用哈希时间锁定进行跨链的原子资产交换，假设Alice和Bob有资产交换的需求，Alice想用1个BTC和Bob换20个ETH. 那么首先需要在两条链上设置哈希时间锁定合约，然后执行如下步骤：

![](/images/15532695517070.png)

1. Alice 随机构建一个字符串s，并计算出其哈希 h = hash(s)；
2. Alice 将h发送给Bob的合约；
3. Alice锁定自己的1个BTC资产，并设置一个较长的锁定时间t1, 并设置了获取该BTC的一个条件：谁能够提供h的原始值s就可以得到该BTC;
4. Bob观察到Alice 合约中锁定了一个BTC, 然后Bob锁定自己的20个ETH资产，并设置一个相对较短的锁定时间t2, t2 < t1, Bob也设置了同样获取条件（谁提供h的原始值s就可以获取20个ETH）；
5. Alice将自己最初生成的字符串s 发送到Bob的合约里取得了20个ETH;
6. Bob观察到步骤5中Alice的s值，将其发送给Alice的合约成功获取1个BTC; 至此Alice和Bob完成了资产的交换。

哈希时间锁定合约也有一些约束条件： 时间设置需要有时间差， 只适合偏资产或者关键数据的交换，在支付领域较多，例如闪电网络、雷电网络以及跨链资产转移协议Interledger等。

明天在介绍 侧链/中继链

## 侧链/中继链（Sidechains / Relays）

侧链是指完全拥有某链的功能的另一条区块链，侧链可以读取和验证主链上的信息。主链不知道侧链的存在，由侧链主动感知主链信息并进行相应的动作。而中继链则是侧链和公证人机制的结合体，中继链具有访问需要和验证进行互操作的链的关键信息并对两条链的跨链消息进行转移。从这个角度看中继链也是一种去中心的公证人机制。





https://tech.hyperchain.cn/blockchain-interoperability/?from=timeline

