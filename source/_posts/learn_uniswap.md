---
title: Uniswap 学习记录
date: 2019-03-15 22:59:27
categories: 学习
tags:
    - 学习
author: Tiny熊
---

Uniswap 协议

## 定义

Uniswap 是一个以太坊上运行的去中心化交易所协议，能让 ETH 和 ERC20 代币之间的兑换变得非常简易。

## 机制

Uniswap 用一个被称为“自动做市商”（AMM）的模型，根据可用的流动性自动调整兑换比率。

Uniswap 使用了一个由 Vitalik 提出的“恒定乘积做市商”的模型，能让在合约中锁定的两种资产之间进行交易。

“恒定乘积做市商”使用一个非常简单的公式 x*y=k，其中 x 是 ETH，y 是 ERC20 代币，k 是恒量。

如果你将所有的 ETH 卖给 Uniswap 合约，仍还有很少量的 ERC20 代币可供购买。例如，如果有人向合约出售了1个 ETH，现在总共有11个 ETH。为了保持 k 恒定，就需要有 500/11 = 45.45 个 ERC20 代币。所以你要给发送 50 - 45.45 = 4.55 个 ERC20 代币给买家。

成为流动性提供者时，同时存入 ETH 和 ERC20 代币，流动性提供者可以得到交易分成。

## Uniswap和 Bancor 的区别
Uniswap和 Bancor 的区别：

![](/images/15526622474123.jpg)

## 其他

目前 Uniswap 流动性池中有2万个ETH， Uniswap代币兑换是及时的。
Uniswap合约使用Vyper开发，所有内容只有创始人（Hayden）一个全职开发者。


## 参考

https://mp.weixin.qq.com/s/15UWTVRHVLU3DCyR48zh_w

