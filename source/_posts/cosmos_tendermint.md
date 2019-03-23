---
title: Cosmos & Tendermint
date: 2019-03-15 22:59:27
categories: 学习
tags:
    - 学习
author: Tiny熊
---

Cosmos 和 Polkadot 的设计有很多相似之处，还有国内团队AckBlock的Forge，今天好好看了看Cosmos

## cosmos & tendermint

Cosmos的人认为： 很多人（组织）会想拥有一条属于自己的链，通过 tendermint通用的区块链开发框架，快速定制开发自己的链。

一条链包括3个部分的话：网络层，共识层，应用层。

tendermint 包含两部分：

1. tendermint core 把共识层和网络层封装在了一起，共识层是拜占庭共识算法+pos。
2. ABCI协议，Application Blockchain Interface，  tendermint core 引擎和上面开发者自定义的应用层之间的接口。  

Cosmos SDK 是实现ABCI协议，如 区块链中的一些通用模块标准化，这些通用模块覆盖了大部分应用层需要具备的功能，比如：staking（抵押机制）、slashing（惩罚机制）、IBC（跨链功能），账户accounts、治理、奖励&手续费等。

**跨链** 有很多条链的时候，跨链问题就来了， comos 抽象出来一个 机制抽象 IBC协议，Inter-Blockchain Communication。IBC就像一座桥，让不同的链可以互相连通（支持简单的价值传递）。


有了IBC这个跨链通信协议，我们如何构造一个互联互通的区块链网络？

1. 两两相连
2. 单连跨链验证

cosmos采用另一种办法跨链。他们采用一种模块化的架构来建立整个区块链网络的连接，这个架构包括两个组成部分：一个叫hub，一个叫zone。

后续进一步讲究

## 参考

[Cosmos上线主网了，但是“为什么需要跨链”依然有待探寻](https://mp.weixin.qq.com/s/az2XnCJDdMi3LrukKY3ypQ)


