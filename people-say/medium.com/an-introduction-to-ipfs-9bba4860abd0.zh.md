
-   `author:` <https://medium.com/@ConsenSys?source=post_header_lockup>
-   `url:` <https://medium.com/@ConsenSys/an-introduction-to-ipfs-9bba4860abd0>

* * *

<details>

<summary> 目录 </summary>

<!-- START doctoc -->

<!-- END doctoc -->

</details>

# **IPFS简介**

![](https://cdn-images-1.medium.com/freeze/max/60/1*czZJ7mvEAqL4wNAg-jt9Ow.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*czZJ7mvEAqL4wNAg-jt9Ow.jpeg)

信用: Bogdan Burcea

"当你有[IPFS](https://ipfs.io/),你可以用一种特定的方式开始查看其他所有内容,并且你意识到你可以全部替换它" -[Juan Benet](https://www.google.com/?gws_rd=ssl#q=juan+benet+ipfs)

#### IPFS的技术方法较少

来自John Lilic

本节将尝试提供高水平的洞察力,作为我的同事,Christian Lundkvist博士的前奏,深入下面. [dive technical summary](http://whatdoesthequantsay.com/2015/09/13/ipfs-introduction-by-example/)IPFS最初是由Juan Benet努力建立一个能够快速移动版本化科学数据的系统. 

使您能够跟踪软件状态随时间的变化 ([Versioning](https://en.wikipedia.org/wiki/Software_versioning)) . [think Git](https://en.wikipedia.org/wiki/Git_%28software%29)IPFS从此被认为是;[The Distributed, Permanent Web](https://ipfs.io/ipfs/QmNhFJjGcMPqpuYfxL62VVB9528NXqDNMFXiqN5bgFYiZ1/its-time-for-the-permanent-web.html)"IPFS是一种分布式文件系统,旨在将所有计算设备与相同的文件系统连接起来. *在某些方面,这类似于Web的原始目标,但IPFS实际上更类似于交换git对象的单个bittorrent swarm. *IPFS可以成为互联网的一个新的主要子系统. 如果构建正确,它可以补充或替换HTTP. 它可以补充或替代更多. 听起来很疯狂. 真是太疯狂了. "\[][1](https://ipfs.io/ipfs/QmNhFJjGcMPqpuYfxL62VVB9528NXqDNMFXiqN5bgFYiZ1/its-time-for-the-permanent-web.html)IPFS的核心是一个版本化文件系统,它可以接收文件并对其进行管理,并将它们存储在某个地方,然后随着时间的推移跟踪版本. 

IPFS还考虑了这些文件在网络中的移动方式,因此它也是一个分布式文件系统. IPFS规定了数据和内容如何在网络上移动,其性质与bittorrent相似. 

此文件系统层提供了非常有趣的属性,例如: -

完全分发的网站-

没有原始服务器的网站-

可以完全在客户端浏览器上运行的网站-

没有任何服务器可以与之交谈的网站内容寻址

**IPFS不是引用存储服务器的对象 (图片,文章,视频) ,而是通过文件上的哈希引用所有内容. **

我们的想法是,如果在您的浏览器中您想要访问特定页面,那么IPFS将询问整个网络"是否有人拥有与此哈希对应的文件?"并且IPFS上的节点可以返回允许您访问的文件它. 

IPFS在HTTP层使用内容寻址. 这是一种说法,而不是创建一个按位置处理事物的标识符,我们将通过内容本身的某种表示来解决它. 这意味着内容将决定地址. 机制是获取一个文件,以加密方式对其进行哈希处理,以便最终得到一个非常小且安全的文件表示,这样可以确保某人不能只提出具有相同哈希值的另一个文件并将其用作地址. IPFS中的文件地址通常以标识某个根对象的散列开始,然后是向下走的路径. 您正在与特定对象进行通信,而不是服务器,然后您正在查看该对象中的路径. 

**HTTP与IPFS一起查找和检索文件HTTP有一个很好的属性,其中标识符是位置,因此很容易找到托管文件的计算机并与它们通信. **

这很有用,通常可以很好地工作,但不能用于离线情况,也不能用于希望最大限度地减少网络负载的大型分布式场景. 在IPFS中,您将步骤分为两部分;

识别具有内容寻址的文件

1.  去找到它 - 当你有哈希然后你问你所连接的网络'谁有这个内容?
2.   (hash) '然后连接到相应的节点并下载它. 结果是对等覆盖,为您提供非常快速的路由. 

要了解更多信息,请观看

. [Alpha Video](https://www.youtube.com/watch?v=8CMxDNuuAiQ)IPFS示例

#### 来自Christian Lundkvist博士

技术考试和 (行星际文件系统) 是经过良好测试的互联网技术的综合体

,[IPFS](http://ipfs.io/)版本控制系统和[DHTs](https://en.wikipedia.org/wiki/Distributed_hash_table). [Git](https://git-scm.com/)它创建了一个允许交换的P2P群[Bittorrent](https://en.wikipedia.org/wiki/BitTorrent)IPFS对象. *IPFS对象的总体形成加密认证的数据结构,称为a*Merkle DAG这个数据结构可以用来模拟许多其他数据结构. *我们将在本文中介绍IPFS对象和Merkle DAG,并举例说明可以使用IPFS建模的结构. *IPFS对象本质上是一个用于检索和共享的P2P系统

**IPFS对象**

[IPFS](http://ipfs.io/). *IPFS对象是具有两个字段的数据结构: *数据

-   *- 一块大小\<256 kB的非结构化二进制数据. *链接
-   *- 一系列Link结构. *这些是指向其他IPFS对象的链接. 

Link结构有三个数据字段: 

-   *名称*- 链接的名称. 
-   *哈希*- 链接的IPFS对象的哈希值. 
-   *尺寸*- 链接的IPFS对象的累积大小,包括其链接. 

该*尺寸*字段主要用于优化P2P网络,我们在这里大多忽略它,因为从概念上讲,它不需要逻辑结构. 

IPFS对象通常由其Base58编码的哈希引用. 例如,让我们看看带有哈希的IPFS对象*QmarHSr9aSNaPSR6G9KFPbuLV9aEqJfTk1y9B8pdwqK4Rq*使用IPFS命令行工具 (请在家中试试!) : 

\>ipfs对象获取QmarHSr9aSNaPSR6G9KFPbuLV9aEqJfTk1y9B8pdwqK4Rq

{"链接": \[{

"名称": "AnotherName",

"哈希": "QmVtYjNij3KeyGmcgg7yVXWskLaBtov3UYL9pgcGK3MCWu",

"大小": 18},

{"姓名": "SomeName",

"哈希": "QmbUSy8HCn8J4TMDRRdxCbK2uCCtkQyZtY6XYv3y7kLgDC",

"大小": 58}],

"数据": "Hello World!"}

读者可能会注意到所有哈希都以"Qm"开头. 这是因为散列实际上是a**multihash**,这意味着散列本身在multihash的前两个字节中指定散列函数和散列的长度. 在上面的例子中,十六进制的前两个字节是*1220*,哪里*12*表示这是SHA256哈希函数和*20*是以字节为单位的哈希长度--32个字节. 

数据和命名链接为IPFS对象的集合提供了结构**Merkle DAG**-[DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph)意义有向无环图,和[Merkle](https://en.wikipedia.org/wiki/Ralph_Merkle)表示这是一个加密认证的数据结构,它使用加密哈希来处理内容. 作为一个练习,让读者思考为什么在这个图中不可能有循环. 

为了可视化图形结构,我们将通过一个图形来显示IPFS对象,该图形在节点中具有数据,而链接是指向图形边缘到其他IPFS对象,其中链接的名称是图形边缘上的标签. 上面的例子可视化如下: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*9rVlSSzV0efkf18NiYo2eg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1200/1*9rVlSSzV0efkf18NiYo2eg.jpeg)

我们现在将给出可以由IPFS对象表示的各种数据结构的示例. 

#### **文件系统**

IPFS可以轻松表示由文件和目录组成的文件系统

**小文件**

一个小文件 (\<256 kB) 由一个IPFS对象表示*数据*作为文件内容 (加上一个小的页眉和页脚) ,没有链接,即*链接*数组是空的. 请注意,文件名不是IPFS对象的一部分,因此具有不同名称和相同内容的两个文件将具有相同的IPFS对象表示,因此具有相同的哈希. 

我们可以使用该命令向IPFS添加一个小文件*ipfs添加*: 

chris @ chris-VBox: 〜/ tmp $ ipfs add test_dir / hello.txt

添加了QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG test_dir / hello.txt

我们可以使用查看上述IPFS对象的文件内容*ipfs猫*: 

chris @ chris-VBox: 〜/ tmp $ ipfs cat QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG\
你好,世界!

使用查看底层结构*ipfs对象*得到收益率: 

chris @ chris-VBox: 〜/ tmp $ ipfs对象获取QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG

{"链接": \[],

"数据": "\\u0008\\u0002\\u0012\\你好世界!\\ñ\\u0018\\r"}

我们将此文件可视化如下: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*dWuAv67ihETN3FAdzsb87A.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1200/1*dWuAv67ihETN3FAdzsb87A.jpeg)

**大文件**

大文件 (> 256 kB) 由文件块的链接列表表示,文件块的数量小于256 kB,并且只有最小值*数据*指定此对象表示大文件. 指向文件块的链接具有空字符串作为名称. 

chris @ chris-VBox: 〜/ tmp $ ipfs add test_dir / bigfile.js

添加了QmR45FmbVVrixReBwJkhEKde2qwHYaQzGxu4ZoDeswuF9w test_dir / bigfile.js

chris @ chris-VBox: 〜/ tmp $ ipfs object get QmR45FmbVVrixReBwJkhEKde2qwHYaQzGxu4ZoDeswuF9w

{"链接": \[{

"名称":  "",

"哈希": "QmYSK2JyM3RyDyB52caZCTKFR3HKniEcMnNJYdk8DQ6KKB",

"大小": 262158},\
{"名称":  "",

"哈希": "QmQeUqdjFmaxuJewStqCLUoKrR9khqb4Edw9TfRQQdfWz3",

"大小": 262158},

{"名称":  "",

"哈希": "Qma98bk1hjiRZDTmYmfiUXDj8hXXt7uGA5roU5mfUb3sVG",

"大小": 178947}],

"数据": "\\u0008\\u0002\\u0018 \*\\u0010\\u0010\\n"}

![](https://cdn-images-1.medium.com/freeze/max/60/1*bgKkxhSphiCdAF8QKm-oxw.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*bgKkxhSphiCdAF8QKm-oxw.jpeg)

**目录结构**

目录由表示文件或其他目录的IPFS对象的链接列表表示. 链接的名称是文件和目录的名称. 例如,请考虑目录的以下目录结构*test_dir*: 

chris @ chris-VBox: 〜/ tmp $ ls -R test_dir\
test_dir: \
bigfile.js hello.txt my_dir\
测试\_DIR /我的\_目录: \
my_file.txt testing.txt

文件*hello.txt的*和*my_file.txt*两者都包含字符串*你好,世界!\\ñ*. 文件*testing.txt*包含字符串*测试123\\ñ. *

将此目录结构表示为IPFS对象时,它看起来像这样: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*-wVVj4B-YhxvF82iSUrbOQ.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*-wVVj4B-YhxvF82iSUrbOQ.jpeg)

请注意包含该文件的自动重复数据删除*你好,世界!\\N,*此文件中的数据仅存储在IPFS中的一个逻辑位置 (由其哈希处理) . 

IPFS命令行工具可以无缝地跟随目录链接名称来遍历文件系统: 

chris @ chris-VBox: 〜/ tmp $ ipfs cat Qma3qbWDGJc6he3syLUTaRkJD3vAq1k5569tNMbUtjAZjf / my_DIR /我的\_file.txt的\
你好,世界!

**版本化文件系统**

IPFS可以表示Git用于允许版本化文件系统的数据结构. Git提交对象在中描述[Git Book](http://www.git-scm.com/book/en/v2/Git-Internals-Git-Objects#Commit-Objects). 在撰写本文时,未完全指定IPFS Commit对象的结构[discussion is ongoing](https://github.com/ipfs/notes/issues/23). 

Commit对象的主要属性是它有一个或多个带名称的链接*parent0*,*parent1*指向先前提交的等等,以及一个带有名称的链接*目的* (这就是所谓的*树*在Git中) 指向该提交引用的文件系统结构. 

我们举例说明我们以前的文件系统目录结构,以及两个提交: 第一个提交是原始结构,在第二个提交中我们更新了文件*my_file.txt*说*另一个世界!*而不是原来的*你好,世界!. *

![](https://cdn-images-1.medium.com/freeze/max/60/1*84YPXEWxIyuH7WGousjsjg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*84YPXEWxIyuH7WGousjsjg.jpeg)

另请注意,我们有自动重复数据删除功能,因此第二次提交中的新对象只是主目录,即新目录*MY_DIR,*和更新的文件*my_file.txt. *

**Blockchains**

这是IPFS最激动人心的用例之一. 区块链具有自然DAG结构,因为过去的区块总是通过其后来的哈希链接. 比较高级的区块链[Ethereum](https://ethereum.org/)区块链还有一个关联的状态数据库,它有一个[Merkle-Patricia tree](https://github.com/ethereum/wiki/wiki/Patricia-Tree)也可以使用IPFS对象模拟的结构. 

我们假设一个简单的区块链模型,其中每个区块包含以下数据: 

-   事务对象列表
-   前一个块的链接
-   状态树/数据库的哈希

然后可以在IPFS中对此区块链进行建模,如下所示: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*Vk9w5CXlRdp4T10UTpEYXg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*Vk9w5CXlRdp4T10UTpEYXg.jpeg)

我们看到在将状态数据库放在IPFS上时获得的重复数据删除 - 在两个块之间只需要显式存储已更改的状态条目. 

这里有趣的一点是在区块链上存储数据和在区块链上存储数据哈希之间的区别. 在以太坊平台上,您需要为相关状态数据库中的数据存储支付相当大的费用,以便最大限度地减少状态数据库的膨胀 ("区块链膨胀") . 因此,对于较大的数据片段而言,存储的不是数据本身,而是状态数据库中的数据的IPFS散列,这是一种常见的设计模式. 

如果区块链及其关联的状态数据库已经在IPFS中表示,那么在区块链上存储哈希和将数据存储在区块链之间的区别变得有些模糊,因为无论如何一切都存储在IPFS中. 并且块的散列只需要状态数据库的散列. 

在这种情况下,如果有人在区块链中存储了IPFS链接,我们可以无缝地跟随此链接访问数据,就像数据存储在区块链本身一样. 

但是,我们仍然可以区分链上和链外数据存储. 我们通过查看矿工在创建新区块时需要处理的内容来做到这一点. 在当前的以太坊网络中,矿工需要处理将更新状态数据库的事务. 为此,他们需要访问完整的状态数据库,以便能够在更改它的任何地方更新它. 

因此,在IPFS中表示的区块链状态数据库中,我们仍然需要将数据标记为"在链上"或"在链外". 矿工在本地保留以进行开采需要"链上"数据,这些数据将直接受到交易的影响. "脱链"数据必须由用户更新,不需要矿工接触. 

通过[Dr. Christian Lundkvist](https://twitter.com/ChrisLundkvist),工程总监,和[John Lilic](https://twitter.com/johnlilic),ConsenSys Enterprise
