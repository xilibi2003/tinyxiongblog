---
title: 预言机的思考
date: 2019-03-28 23:53:00
categories: 思考
tags:
    - 预言机
author: Tiny熊
---


我们知道所有的数据在经过节点的验证之后，才能上链。
而节点验证达成共识的一个条件是：验证时数据输入是相同的。这让区块链上只能使用链内的确定性的数据，因为链外的数据没法保证在不同的时间进行验证时数据的一致性。

这让区块链和我们的现实世界产生了割裂。

预言机就是这样一座桥（怎么总是喜欢用桥来比喻？），联通着区块链和现实世界。 

如果区块链（智能合约）想要基于某个外部状态做些事情（比如Dai项目依靠外部的币价信息），它不能主动去拿外部数据，而是要依靠**预言机**把外部数据以交易的形式发送进来，从而把一个不确定的数据转化为一个确定的输入。


好了，问题来了，我们说区块链创造了信任，就是因为去中介，现在又引入一个预言机中介，好像是一个讽刺，如何来保证预言机没有作恶呢（加入外部数据是真实的，指如何确保预言机不会篡改外部数据）？


这也是为什么说区块链还在早期，成熟的预言机机制会极大的促进区块链的发展，不少团队正在探索去中心化预言机，未来值得期待。

