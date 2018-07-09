# Ipfs-tour [![explain](http://llever.com/explain.svg)](https://github.com/chinanf-boy/Source-Explain)

「 这里 是关于 `ipfs` 协议 `文献`![china](https://raw.githubusercontent.com/gosquared/flags/master/flags/flags/shiny/24/China.png)`翻译/解释/其他补充`」

> 你问 `这是什么协议`, 比起` http之类`怎么样, 我会说, 这是 **未来**

这段路程会很长很长

[github source](https://github.com/ipfs)

[中文](./readme.md) | [english](https://github.com/ipfs/ipfs)

欢迎 `Issue` 和 `Pull` ❤️, 最好 `Pull` 👏

---

## 生活

[help me live , live need money 💰](https://github.com/chinanf-boy/live-need-money)

---

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->


- [启动时间](#%E5%90%AF%E5%8A%A8%E6%97%B6%E9%97%B4)
- [介绍](#%E4%BB%8B%E7%BB%8D)
  - [电视剧-硅谷](#%E7%94%B5%E8%A7%86%E5%89%A7-%E7%A1%85%E8%B0%B7)
  - [种子-ipfs](#%E7%A7%8D%E5%AD%90-ipfs)
  - [那`ipfs`的软件好了吗](#%E9%82%A3ipfs%E7%9A%84%E8%BD%AF%E4%BB%B6%E5%A5%BD%E4%BA%86%E5%90%97)
  - [如果你还是觉得, what, 什么东西](#%E5%A6%82%E6%9E%9C%E4%BD%A0%E8%BF%98%E6%98%AF%E8%A7%89%E5%BE%97-what-%E4%BB%80%E4%B9%88%E4%B8%9C%E8%A5%BF)
- [更多详细描述与详解](#%E6%9B%B4%E5%A4%9A%E8%AF%A6%E7%BB%86%E6%8F%8F%E8%BF%B0%E4%B8%8E%E8%AF%A6%E8%A7%A3)
  - [1. 万事开头难, 从动手开始](#1-%E4%B8%87%E4%BA%8B%E5%BC%80%E5%A4%B4%E9%9A%BE-%E4%BB%8E%E5%8A%A8%E6%89%8B%E5%BC%80%E5%A7%8B)
    - [1.1 【入门】利用IPFS存放自己的Wiki文件夹 `zhihu`](#11-%E5%85%A5%E9%97%A8%E5%88%A9%E7%94%A8ipfs%E5%AD%98%E6%94%BE%E8%87%AA%E5%B7%B1%E7%9A%84wiki%E6%96%87%E4%BB%B6%E5%A4%B9-zhihu)
  - [2. 从现有产物 p2p 理解](#2-%E4%BB%8E%E7%8E%B0%E6%9C%89%E4%BA%A7%E7%89%A9-p2p-%E7%90%86%E8%A7%A3)
    - [2.1 IPFS网络是如何运行的(p2p网络) `ipfser`](#21-ipfs%E7%BD%91%E7%BB%9C%E6%98%AF%E5%A6%82%E4%BD%95%E8%BF%90%E8%A1%8C%E7%9A%84p2p%E7%BD%91%E7%BB%9C-ipfser)
  - [3. 总有前人种树,与实践](#3-%E6%80%BB%E6%9C%89%E5%89%8D%E4%BA%BA%E7%A7%8D%E6%A0%91%E4%B8%8E%E5%AE%9E%E8%B7%B5)
    - [3.1 下载并玩玩 OpenBazaar, 不打比特币账号随便看看 `app`](#31-%E4%B8%8B%E8%BD%BD%E5%B9%B6%E7%8E%A9%E7%8E%A9-openbazaar-%E4%B8%8D%E6%89%93%E6%AF%94%E7%89%B9%E5%B8%81%E8%B4%A6%E5%8F%B7%E9%9A%8F%E4%BE%BF%E7%9C%8B%E7%9C%8B-app)
    - [3.2 PFS 看片指南：几部IPFS网络中的电影 `video`](#32-pfs-%E7%9C%8B%E7%89%87%E6%8C%87%E5%8D%97%E5%87%A0%E9%83%A8ipfs%E7%BD%91%E7%BB%9C%E4%B8%AD%E7%9A%84%E7%94%B5%E5%BD%B1-video)
  - [4. 小总结看看](#4-%E5%B0%8F%E6%80%BB%E7%BB%93%E7%9C%8B%E7%9C%8B)
    - [4.1 【IPFS】戴嘉乐：详解IPFS的本质、技术架构以及应用 `docs`](#41-ipfs%E6%88%B4%E5%98%89%E4%B9%90%E8%AF%A6%E8%A7%A3ipfs%E7%9A%84%E6%9C%AC%E8%B4%A8%E6%8A%80%E6%9C%AF%E6%9E%B6%E6%9E%84%E4%BB%A5%E5%8F%8A%E5%BA%94%E7%94%A8-docs)
    - [4.2 IPFS 项目内 看看有哪些家族成员(一) `repo`](#42-ipfs-%E9%A1%B9%E7%9B%AE%E5%86%85-%E7%9C%8B%E7%9C%8B%E6%9C%89%E5%93%AA%E4%BA%9B%E5%AE%B6%E6%97%8F%E6%88%90%E5%91%98%E4%B8%80-repo)
    - [4.3 IPFS 项目内 看看有哪些家族成员(二) `repo`](#43-ipfs-%E9%A1%B9%E7%9B%AE%E5%86%85-%E7%9C%8B%E7%9C%8B%E6%9C%89%E5%93%AA%E4%BA%9B%E5%AE%B6%E6%97%8F%E6%88%90%E5%91%98%E4%BA%8C-repo)
- [用户角度的ipfs](#%E7%94%A8%E6%88%B7%E8%A7%92%E5%BA%A6%E7%9A%84ipfs)
  - [开节点, 就是用户](#%E5%BC%80%E8%8A%82%E7%82%B9-%E5%B0%B1%E6%98%AF%E7%94%A8%E6%88%B7)
  - [普通人不会总开节点](#%E6%99%AE%E9%80%9A%E4%BA%BA%E4%B8%8D%E4%BC%9A%E6%80%BB%E5%BC%80%E8%8A%82%E7%82%B9)
  - [filecoin](#filecoin)
- [官方文献](#%E5%AE%98%E6%96%B9%E6%96%87%E7%8C%AE)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

---

## 启动时间

- ⏰ 开始 2018 7.6 

> 刚开始什么都没有, 会有的·

## 介绍

### 电视剧-硅谷

如果你 看到 美剧:硅谷 第三季和第四季, 就会知道, 主角也是在为一个更加自由的网络 `The New Internet`搞搞震.

在我看来, 编剧 创作 这个项目时, 原型有一部分是来自 今天介绍的 [ipfs项目](https://github.com/ipfs/ipfs)

那么恭喜你, 你已经有了一部分了解.

> 十分推荐, 硅谷

### 种子-ipfs

不知道你有没有下过`种子`之类的

> 不要装, 我懂的

我们用快问快答,来 过了这段

- `P2P`,? => 端对端.
- `端`,? => 节点.
- `节点`,? => 你的或别人的电脑
- `节点怎么开`,? => 用`软件`开啊!

### 那`ipfs`的软件好了吗

⏰ 2018 7.9 日 - 今天

浅显一点, 看到上面的 `节点怎么开`的答案没有?!

**软件**

也就是 [ipfs协议团队](https://github.com/ipfs) 要做的, 他们需要把协议 实实在在地变成我们能够运行的 软件

目前有两种可用的软件: 

- 用 `Go 语言`写的 [go-ipfs](https://github.com/ipfs/go-ipfs) `(为主)`
- 用 `js 语言`写的 [js-ipfs](https://github.com/ipfs/js-ipfs)

> 团队英文名: Protocol Labs | [官方](https://protocol.ai/)

### 如果你还是觉得, what, 什么东西

> 上面是我,对自己说的简略的描述, 放开了协议实际实现要面对的问题, 比如各种 分布式什么啊, git文件, 唯一文件ID 一堆堆


## 更多详细描述与详解

<b>那么我们重新开始吧 🖐️</b>

> 本文下面链接, 是参考文献, 请跟着顺序来走啦

### 1. 万事开头难, 从动手开始

#### 1.1 [【入门】利用IPFS存放自己的Wiki文件夹](https://zhuanlan.zhihu.com/p/33163010) `zhihu`

> 很遗憾, https://ipfs.io 官方要翻墙, 也因为如此 `ipfs` 的 国内 测试/使用 受到阻碍

### 2. 从现有产物 p2p 理解

#### 2.1 [IPFS网络是如何运行的(p2p网络)](http://ipfser.org/2018/01/17/r17/) `ipfser`

### 3. 总有前人种树,与实践

#### 3.1 [下载并玩玩 OpenBazaar, 不打比特币账号随便看看](https://openbazaar.org/) `app`

> `OpenBazaar`是 IPFS 上的一个明星应用,开放集市,黑市, 货币主要是比特币

> 关于[比特币与区块链是什么 可以看看](https://github.com/chinanf-boy/what-is-bitcoin)

#### 3.2 [PFS 看片指南：几部IPFS网络中的电影](http://ipfser.org/2018/04/08/r36/) `video`

> 哎, 不要想歪洛🤫

### 4. 小总结看看

#### 4.1 [【IPFS】戴嘉乐：详解IPFS的本质、技术架构以及应用](http://ipfser.org/2018/03/28/r33/) `docs`

#### 4.2 [IPFS 项目内 看看有哪些家族成员(一)](http://ipfser.org/2018/02/03/23/) `repo`

#### 4.3 [IPFS 项目内 看看有哪些家族成员(二)](http://ipfser.org/2018/03/02/r26/) `repo`

## 用户角度的ipfs

ipfs 的愿景之一, 就是在将来某一天能取代 `http 协议`. 自然而然, 要取代一个协议, ipfs 本身也属于一份协议

> `http://***` => `ipfs://***`

但是, 这关用户什么事情了 ❓, 难道你还想每个用户都了解 ipfs 协议, 像如今使用的 http协议, 可以说大部分人都不
需要了解它是什么❓❕

仅仅只需要知道: 

- `http://www.baidu.com` 哦😯 => `你百度一下啦`
- `http://www.taobao.com` 哦😯  => `你上淘宝找找`

> 又或者 微博,QQ 诸如此类

所以, 2018 7.9 日 ,就在今天. ipfs 还没准备好,向全世界的人们推广

### 开节点, 就是用户

ipfs 作为 p2p 网络, 每个节点都是平等的, 

- 要从节点网络 `获取`数据, 开节点先
- 要`存入`数据到 节点网络, 开节点先

拿 普遍的 http 协议端口:80 来说, 客户端要连上 服务器的80端口,从中获取网页文档 

开节点软件的同时, 软件在特定端口上等待与其他节点网络的互通 

> `p2p => 端对端 => 端口对端口`

### 普通人不会总开节点

再从 种子的 角度来看, 基本我们使用 种子下载器, 下完自然就结束啦

对应到, ipfs 网络, 我们就是开节点, 下载数据, 关节点

但是问题是, 每个人都这样, ipfs 网络也就没有持续发展下去的地基 - 节点网络

开节点,如果有人从你这里获取数据, 自然而然, 你的上传带宽会被占用

你会无偿给人, 提供带宽吗 ?, 这想想都不可能!

最后, 能长期开放节点, 不就和现在 各个公司服务器 一样多 而已

也就失去了, 替换 http 协议的

- `慢` - 多个路由转
- `独大` - 公司获取你个人所有数据
- `不安全` - 没有 https 之前, http的安全性就是个笑话
- ...

**那, 如果不是无偿的呢**

### filecoin

在我看来, ipfs 团队应对这个关于 无偿开节点的 问题的, 解决方式就是

**有偿开节点** 不就可以了吗

显然, 比特币 的特性 和 热度 都如此明显, 那就 创造新的比特币 就好了

`filecoin` 概念 诞生了

> filecoin 目前仍在开发中,[官网](https://filecoin.io/)

如果你理解 比特币和区块链 问题, 就会知道 区块装的是交易记录

> 不理解的 看[比特币与区块链是什么](https://github.com/chinanf-boy/what-is-bitcoin)

但, `filecoin` 的 概念, 我简要描述一下, 就是 你 提供/上传/存储 数据, 能分配到 `filecoin`

一句话说， `filecoin`是 奖赏给 长期提供节点的用户的 比特币, 衡量的标准是 提供/上传/存储 数据

> 不过听说, 下载也需要 `filecoin` , 我觉得这点上, 中国不太能接·受 毕竟我们太多免费的了


## 官方文献

- `ipfs的白皮书` [中文](https://gguoss.github.io/2017/05/28/ipfs/) | [原文 en](https://github.com/ipfs/papers/raw/master/ipfs-cap2pfs/ipfs-p2p-file-system.pdf)

- `filecoin的白皮书` [中文](http://chainx.org/paper/index/index/id/13.html) | [原文 en](https://filecoin.io/filecoin.pdf)