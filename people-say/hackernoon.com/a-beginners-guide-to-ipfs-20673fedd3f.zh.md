
-   `author:` <https://hackernoon.com/@kojoaddaquay?source=post_header_lockup>
-   `url:` <https://hackernoon.com/a-beginners-guide-to-ipfs-20673fedd3f>

* * *

<details>

<summary> 目录 </summary>

<!-- START doctoc -->

<!-- END doctoc -->

</details>

# IPFS初学者指南

![](https://cdn-images-1.medium.com/freeze/max/60/1*0kGmNu9xBXUUMRC9BdAJhQ.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*0kGmNu9xBXUUMRC9BdAJhQ.jpeg)

在我以前[post](https://medium.com/@kojoaddaquay/decentralizing-the-sharing-economy-a-review-of-the-origin-protocol-bf0003334233),我们讨论了共享经济的未来以及可能是塑造它的核心的令人兴奋的创新. 提到的关键技术之一是行星际文件系统 (IPFS) . 它是一个点对点 (p2p) 文件共享系统,旨在从根本上改变信息在全球各地的分布方式. IPFS由通信协议和分布式系统中的若干创新组成,这些创新已被组合以产生与众不同的文件系统. 因此,要了解IPFS正在努力实现的全面广度和深度,了解实现这一目标的技术突破非常重要. 

### **通信协议和分布式系统**

对于两个人交换信息,他们需要通用的规则集来定义信息的传输方式和时间. 这些规则被广泛地称为通信协议,但这非常令人满意,所以我们简单地将其称为语言. 如果你去过一个你不会说母语的外国,你可能会遇到通信协议的失败 (或缺乏) . 计算机就是这种情况;他们无法相互通信,并且作为孤立的计算设备存在,直到20世纪80年代早期,当时发明了第一个计算通信协议. 

> *"协议是将计算语言与计算通信联系起来"*

在计算机中,通信协议通常存在于多个层的捆绑 (称为协议套件) 中. 例如,[Internet protocol](https://en.wikipedia.org/wiki/Internet_Protocol)套件由4层组成,每层都负责特定的功能. 除了通信协议之外,要理解的重要关系是计算机之间互连的基本结构. 这被称为[system architecture](https://en.wikipedia.org/wiki/Distributed_computing). 有几种存在,但与我们相关的两种类型是**客户端服务器**和**点对点网络**. 

互联网主要是客户端 - 服务器关系,它依赖于Internet协议套件. 其中,超文本传输​​协议 ([HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)) 是沟通的基础. 

数据存储在集中式服务器中,并通过基于位置的寻址进行访问. 这样可以更轻松地分发,管理,保护数据,并扩展服务器和客户端的容量. 然而,在安全性,隐私性和效率领域存在许多弱点: 服务器的控制转换为对数据的控制. 这意味着任何控制服务器的一方都可以访问,更改和删除您的数据;这可能是对服务器或恶意黑客具有合法权限的实体. 在基于位置的寻址中,数据通过它所在的位置而不是其内容来识别. 此限制意味着您必须一直到特定位置访问一段数据,即使相同的数据可以在更近的地方获得. 也无法判断数据是否已被更改,因为客户端只需知道它在哪里,而不是它是什么. 

但是客户端 - 服务器模型和HTTP在其大部分历史中都非常可靠地服务于互联网. 这是因为HTTP Web非常有效地移动文本和图像等小文件. 在网络的前二十年中,平均网页的大小仅从~2千字节增加到大约2兆字节. 

![](https://cdn-images-1.medium.com/freeze/max/60/0*k3xpoGddpv_Ke6dR.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*k3xpoGddpv_Ke6dR.)

[Source](http://www.websiteoptimization.com/speed/tweak/average-web-page/growth-average-web-page2014.png)

HTTP非常适合加载网站,但它不是为传输大量数据 (如音频和视频文件) 而设计的. 这些限制可能使得Napster (音乐) 和BitTorrent (电影和几乎任何东西) 等替代文件共享系统的出现和主流成功. 

快进到2018年,按需高清视频流和大数据正在变得无处不在;我们正在继续向上生产/消费越来越多的数据,同时开发越来越强大的计算机来处理它们. 云计算的重大进步有助于维持这种转变,但分发所有这些数据的基础设施基本保持不变. 

### **行星际文件系统**

IPFS试图通过一种新颖的p2p文件共享系统来解决客户端 - 服务器模型和HTTP Web的不足. 该系统综合了几项新的和现有的创新. IPFS是一个开源项目[Protocol Labs](https://protocol.ai/),一个网络协议的研发实验室和前Y Combinator初创公司. Protocol Labs还开发了类似的补充系统[IPLD](https://ipld.io/)和[Filecoin](https://coincentral.com/filecoin-beginners-guide-largest-ever-ico/),这将在下面解释. 全世界数以百计的开发人员为IPFS的发展做出了贡献,因此其编排工作是一项艰巨的任务. 以下是主要组件: 

**分布式哈希表**

一个[hash table](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/)是一种将信息存储为键/值对的数据结构. 在分布式哈希表 (DHT) 中,数据分布在计算机网络上,并且有效地协调以实现节点之间的有效访问和查找. 

DHT的主要优点在于分散,容错和可扩展性. 节点不需要集中协调,即使节点发生故障或离开网络,系统也能可靠地运行,DHT可以扩展以容纳数百万个节点. 这些特征一起导致系统通常比客户端 - 服务器结构更具弹性. 

**阻止交换**

流行的文件共享系统Bittorrent能够通过依赖创新的数据交换协议成功协调数百万个节点之间的数据传输,但它仅限于洪流生态系统. IPFS实现了该协议的通用版本,称为BitSwap,它作为任何类型数据的市场运行. 这个市场是基础[Filecoin](https://filecoin.io/): 基于IPFS构建的p2p存储市场. 

**Merkle DAG**

merkle DAG是一种混合物[Merkle Tree](https://hackernoon.com/merkle-trees-181cb4bc30b4)和有向无环图 ([DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph)) . Merkle树确保在p2p网络上交换的数据块是正确的,未损坏的和不变的. 通过使用组织数据块来完成此验证[cryptographic hash](https://simple.wikipedia.org/wiki/Cryptographic_hash_function)功能. 这只是一个函数,它接受输入并计算与该输入相对应的唯一字母数字字符串 (哈希) . 很容易检查输入是否会产生给定的散列,但很难猜测来自散列的输入. 

![](https://cdn-images-1.medium.com/freeze/max/60/0*E7FAXhmHiZlQ6YJb.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*E7FAXhmHiZlQ6YJb.)

不要混淆这两个. 资源: <http://www.merkletrees.org/>

各个数据块称为"叶节点",它们被散列形成"非叶节点". 然后可以组合和散列这些非叶节点,直到所有数据块可以由单个根散列表示. 这是一种更简单的概念化方法: 

![](https://cdn-images-1.medium.com/freeze/max/60/0*aStXJqYfNcFgn-j1.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*aStXJqYfNcFgn-j1.)

DAG是一种模拟没有周期的拓扑信息序列的方法. DAG的简单示例是家谱. merkle DAG基本上是一种数据结构,其中哈希用于引用DAG中的数据块和对象. 这创建了几个有用的功能: IPFS上的所有内容都可以唯一标识,因为每个数据块都有唯一的哈希. 此外,数据是防篡改的,因为改变它会改变散列,如下所示: 

![](https://cdn-images-1.medium.com/freeze/max/60/0*AiVQ5qZOV2WcrHDJ.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*AiVQ5qZOV2WcrHDJ.)

资源: [ethereum.org](https://blog.ethereum.org/2014/02/18/ethereum-scalability-and-decentralization-updates/)

IPFS的核心原则是对广义的merkle DAG上的所有数据进行建模. 这种安全功能的重要性很难夸大. 为了与客户端 - 服务器系统进行比较,请看这个人[hacked 40 websites in 7 minutes](https://hackernoon.com/how-i-hacked-40-websites-in-7-minutes-5b4c28bc8824). 

**版本控制系统**

Merkle DAG结构的另一个强大功能是它允许您构建分布式版本控制系统 ([VCS](https://en.wikipedia.org/wiki/Distributed_version_control)) . 最受欢迎的例子是Github,它允许开发人员轻松地同时协作项目. Github上的文件使用merkle DAG进行存储和版本化. 它允许用户独立复制和编辑文件的多个版本,存储这些版本以及稍后将编辑与原始文件合并. 

IPFS对数据对象使用类似的模型: 只要对应于原始数据的对象和任何新版本都可访问,就可以检索整个文件历史记录. 鉴于数据块通过网络本地存储并且可以无限期缓存,这意味着可以永久存储IPFS对象. 

此外,IPFS不依赖于对Internet协议的访问. 数据可以分发[overlay networks](https://en.wikipedia.org/wiki/Overlay_network),这只是建立在另一个网络上的网络. 这些功能值得注意,因为它们是抗审查网络的核心要素. 它可以成为促进言论自由以对抗流行的有用工具[internet censorship](http://www.visualcapitalist.com/internet-censorship-map/)世界各地,但我们也应该认识到不良行为者滥用的可能性. 

**自我认证文件系统**

我们将介绍IPFS的最后一个重要组成部分是自我认证文件系统 ([SFS](https://en.wikipedia.org/wiki/Self-certifying_File_System)) . 它是一个分布式文件系统,不需要特殊的数据交换权限. 它是"自我认证",因为提供给客户端的数据是通过文件名 (由服务器签名) 进行身份验证的. 结果?您可以使用本地存储的透明度安全地访问远程内容. 

IPFS以此概念为基础,创建了行星间名称空间 (IPNS) . 它是一个使用的SFS[public-key cryptography](https://medium.com/@vrypan/explaining-public-key-cryptography-to-non-geeks-f0994b3c2d5)自我认证网络用户发布的对象. 我们之前提到IPFS上的所有对象都可以唯一标识,但这也扩展到节点. 网络上的每个节点都有一组公钥,私钥和一个节点ID,它是其公钥的哈希值. 因此,节点可以使用其私钥来"签署"他们发布的任何数据对象,并且可以使用发件人的公钥来验证此数据的真实性. 

**以下是关键IPFS组件的快速回顾: **

-   使用分布式哈希表,节点可以存储和共享数据,而无需中央协调
-   IPNS允许使用公钥加密技术立即预先验证和验证交换的数据. 
-   Merkle DAG可实现唯一标识,防篡改和永久存储的数据
-   您可以通过版本控制系统访问已编辑数据的过去版本

![](https://cdn-images-1.medium.com/freeze/max/60/0*erhuY4fEfd3PA4Im.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*erhuY4fEfd3PA4Im.)

简单的概念框架

**那么为什么这一切都很重要?**

IPFS提供高吞吐量,低延迟,数据分发. 它也是分散和安全的. 这开辟了几个有趣且令人兴奋的用例. 它可用于向网站提供内容,通过自动版本控制和备份全局存储文件,促进安全的文件共享和加密通信. 

以下是一些在IPFS上构建的有趣项目: 

[Akasha](https://akasha.world/),*下一代社交网络*

[Balance3](https://www.balanc3.net/#/),*一个三重进入的会计平台*

[BlockFreight](https://blockfreight.com/),*全球货运的开放网络*

[Digix](https://digix.global/),*用于标记实物黄金的平台*

[Infura](https://infura.io/),*DApps的基础设施提供商*

[Livepeer](https://livepeer.org/),*分散的实时视频流媒体平台*

[Origin](https://www.originprotocol.com/en),*共享经济的点对点市场*

[uPort](https://www.uport.me/),*自我主权身份系统*

这些应用程序的多样性证明了IPFS在多种不同用例中的多功能性. 它还被用作公共区块链和其他p2p应用程序的补充文件系统. 在撰写本文时,在以太坊智能合约中存储一千字节的数据可能需要花费数美元. 这是一个主要的制约因素,目前正在推出新的分散式应用程序 (DApps) . IPFS可与智能合约和区块链数据互操作,因此可为以太坊生态系统增加可靠,低成本的存储容量. 在IPFS上本地可以访问的以太坊区块链数据的尝试是一个单独的协议,称为[IPLD](https://ipld.io/) (行星际关联数据) . 

**挑战**

尽管IPFS表现令人印象深刻,但仍有一些问题尚未完全解决. 首先,IPNS上的内容寻址目前不是非常用户友好. 您的典型IPNS链接如下所示: 

*ipfs.io/ipns/QmeQe5FTgMs8PNspzTQ3LRz1iMhdq9K34TQnsCP2jqt8wV/*

可以使用域名系统 (DNS) 将这些链接缩短为更简单的名称,但这会为内容分发引入外部故障点. 但是,仍然可以通过原始IPNS地址访问内容. 一些用户还报告IPNS在解析域名方面可能很慢,延迟时间可达数秒. 目前尚不清楚这个问题的根本究竟是什么. 

*更新*: *在03/26/2018,IPNS发布了一个带有实验性功能的升级,以加快发布/解析. 详细信息* [*here*](https://blog.ipfs.io/34-go-ipfs-0.4.14#ipns-improvements)

在IPFS上,节点也很少有动力维持网络上数据的长期备份. 节点可以选择清除缓存数据以节省空间,这意味着如果没有剩余节点托管数据,理论上文件最终会"消失". 在目前的采用水平上,这不是一个重要问题,但从长远来看,备份大量数据需要强有力的经济激励. 

**存储市场**

Filecoin是一个单独的协议,旨在为IPFS上的文件存储添加经济激励,并建立一个可与企业云存储 (如Amazon S3等) 相媲美的分布式存储市场. IPFS + FileCoin不是采用固定价格的集中式基础设施,而是在本地提供商的全球网络上提供存储,这些提供商可以根据供需情况自由设定价格. 代替[Proof-of-Work](https://en.wikipedia.org/wiki/Proof-of-work_system)像比特币这样的共识算法,Filecoin使用[Proof-of-Storage](https://filecoin.io/filecoin.pdf)确保安全性和可靠性. 因此,任何人都可以加入网络,在其计算设备上提供未使用的硬盘空间,并获得用于数据存储和检索服务的Filecoin令牌奖励. 

该网络正在以太坊开发,因此智能合约集成可以在存储市场中产生诸如托管,保险等高级功能. 理论上,这种经济模型应该发展一个竞争激烈的自由市场,其成本可能比大型供应商低. 但FileCoin还没有推出,所以观察这些概念在现实中如何发挥将是有趣的. 

**入门**

IPFS是一项雄心勃勃的努力,显然,系统功能的精确机制远比本指南中描述的要复杂得多. 我们将为密码学家和计算机科学家留下这些细节. 你不必是专家*使用*IPFS,所以如果任何优势或用例看起来有用或吸引你,请下载IPFS并开始使用[here](https://ipfs.io/docs/getting-started/). 如果您有未使用存储的千兆字节或太字节,并且想要充分利用该空闲容量,您可以[sign up](https://docs.google.com/forms/d/e/1FAIpQLSfdFpWhJj8OIGA2iXrT3bnLgVK9bgR_1iLMPdAcXLxr_1d-pw/viewform?c=0&w=1)在网络发布时成为早期的Filecoin矿工. 你也可以[sign up](https://docs.google.com/forms/d/e/1FAIpQLSdCOjMenUU7WtT54zeAivCS2nnaWYQIgaXh0eRdIdpi6Pwkew/viewform)如果您有兴趣成为早期存储用户. 

使用IPFS是非常了不起的,理解使其成为可能的技术魔法更令人兴奋. 如果成功,IPFS及其补充协议可以为下一代网络提供弹性基础设施. 承诺分发,安全和透明的网络. 

* * *

*来源*

科默,道格拉斯. *计算机网络和互联网*. 皮尔森,2015年. [goo.gl/AbM8st](http://goo.gl/AbM8st)

IPFS白皮书 (草案3) <http://goo.gl/zwKD9J>

Filecoin白皮书<https://goo.gl/RrxcvX>
