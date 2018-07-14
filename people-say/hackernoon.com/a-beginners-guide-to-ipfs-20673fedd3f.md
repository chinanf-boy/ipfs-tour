- `author:` https://hackernoon.com/@kojoaddaquay?source=post_header_lockup
- `url:` https://hackernoon.com/a-beginners-guide-to-ipfs-20673fedd3f

---

<details>

<summary> 目录 </summary>

<!-- START doctoc -->
<!-- END doctoc -->


</details>


A Beginner’s Guide to IPFS
==========================

![](https://cdn-images-1.medium.com/freeze/max/60/1*0kGmNu9xBXUUMRC9BdAJhQ.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*0kGmNu9xBXUUMRC9BdAJhQ.jpeg)

In my previous [post](https://medium.com/@kojoaddaquay/decentralizing-the-sharing-economy-a-review-of-the-origin-protocol-bf0003334233), we discussed the future of the sharing economy and the exciting innovations that could be central to shaping it. One of the key technologies mentioned was the Interplanetary File System (IPFS). It’s a peer-to-peer (p2p) filesharing system that aims to fundamentally change the way information is distributed across & beyond the globe. IPFS consists of several innovations in communication protocols and distributed systems that have been combined to produce a file system like no other. So to understand the full breadth and depth of what IPFS is trying to achieve, it’s important to understand the tech breakthroughs that make it possible.

### **Communication Protocols & Distributed Systems**

For two people to exchange information, they need common sets of rules that define how & when information is transmitted. These rules are broadly known as communication protocols, but that’s quite a mouthful so we simply call it language. If you’ve ever been to a foreign country where you don’t speak the native tongue, you’ve probably experience a failure (or lack) of communication protocols. This was the case with computers; they were unable to communicate with each other and existed as isolated computational devices until the early 1980’s when the first communication protocols for computing were invented.

> _“protocols are to communication what programming languages are to computations”_

In computers, communication protocols usually exist in bundles (called a protocol suite) of several layers. For example, the [Internet protocol](https://en.wikipedia.org/wiki/Internet_Protocol) suite consists of 4 layers, each of which is responsible for specific functions. In addition to communication protocols, an important relationship to understand is the basic structure of the interconnections between the computers. This is known as the [system architecture](https://en.wikipedia.org/wiki/Distributed_computing). Several exist, but the two types relevant to us are **client-server** and **peer-to-peer networks**.

The internet is dominated by client-server relationships, which rely on the Internet Protocol suite. Of these, Hypertext Transfer Protocol ([HTTP](https://en.wikipedia.org/wiki/Hypertext_Transfer_Protocol)) is the basis for communication.

Data is stored in centralized servers and accessed by location-based addressing. This makes it easier to distribute, manage, secure the data, and to scale the capacity of both servers and clients. However there are many weaknesses in the realms of security, privacy and efficiency: control of the server translates to control of the data. This means your data can be accessed, altered and removed by any party with control of the server; this could be an entity with legitimate authority over the server or a malicious hacker. In location-based addressing, data is identified by where it is located rather its content. This limitation means you have to go to all the way to specific location to access a piece of data, even if that same data is available somewhere closer. There is also no way of telling if the data has been altered, since the client only needs to know where it is, not what it is.

But the client-server model and HTTP have served the internet pretty reliably for most of its history. This is because the HTTP web is highly effective for moving around small files like text and images. In the first two decades of the web, the size of the average web page has only increased from ~2 kilobytes to ~2 megabytes.

![](https://cdn-images-1.medium.com/freeze/max/60/0*k3xpoGddpv_Ke6dR.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*k3xpoGddpv_Ke6dR.)

[Source](http://www.websiteoptimization.com/speed/tweak/average-web-page/growth-average-web-page2014.png)

HTTP is great for loading websites but it wasn’t designed for the transfer of large amounts data (like audio and video files). These constraints possibly enabled the emergence and mainstream success of alternative filesharing systems like Napster (music) and BitTorrent (movies and pretty much anything).

Fast forward to 2018, where on-demand HD video streaming and big data are becoming ubiquitous; we are continuing the upward march of producing/consuming more and more data, along with developing more and more powerful computers to process them. Major advancements in cloud computing have helped sustain this transition, however the fundamental infrastructure for distributing all this data has remained largely the same.

### **The InterPlanetary File System**

IPFS attempts to address the deficiencies of the client-server model and HTTP web through a novel p2p file sharing system. This system is a synthesis of several new and existing innovations. IPFS is an open-source project created by [Protocol Labs](https://protocol.ai/), an R&D lab for network protocols and former Y Combinator startup. Protocol Labs also develops complementary systems like [IPLD](https://ipld.io/) and [Filecoin](https://coincentral.com/filecoin-beginners-guide-largest-ever-ico/), which will be explained below. Hundreds of developers around the world contributed to the development of IPFS, so its orchestration has been a massive undertaking. Here are the main components:

**Distributed Hash Tables**

A [hash table](https://www.hackerearth.com/practice/data-structures/hash-tables/basics-of-hash-tables/tutorial/) is a data structure that stores information as key/value pairs. In distributed hash tables (DHT) the data is spread across a network of computers, and efficiently coordinated to enable efficient access and lookup between nodes.

The main advantages of DHTs are in decentralization, fault tolerance and scalability. Nodes do not require central coordination, the system can function reliably even when nodes fail or leave the network, and DHTs can scale to accommodate millions of nodes. Together these features result in a system that is generally more resilient than client-server structures.

**Block Exchanges**

The popular file sharing system Bittorrent is able to successfully coordinate the transfer of data between millions of nodes by relying on an innovative data exchange protocol, however it is limited to the torrent ecosystem. IPFS implements a generalized version of this protocol called BitSwap, which operates as a marketplace for any type of data. This marketplace is the basis for [Filecoin](https://filecoin.io/): a p2p storage marketplace built on IPFS.

**Merkle DAG**

A merkle DAG is a blend of a [Merkle Tree](https://hackernoon.com/merkle-trees-181cb4bc30b4) and a Directed Acyclic Graph ([DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph)). Merkle trees ensure that data blocks exchanged on p2p networks are correct, undamaged and unaltered. This verification is done by organizing data blocks using [cryptographic hash](https://simple.wikipedia.org/wiki/Cryptographic_hash_function) functions. This is simply a function that takes an input and calculates a unique alphanumeric string (hash) corresponding with that input. It is easy to check that an input will result in a given hash, but incredibly difficult to guess the input from a hash.

![](https://cdn-images-1.medium.com/freeze/max/60/0*E7FAXhmHiZlQ6YJb.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*E7FAXhmHiZlQ6YJb.)

Don’t confuse these two. Source: [http://www.merkletrees.org/](http://www.merkletrees.org/)

The individual blocks of data are called ‘leaf nodes’, which are hashed to form ‘non-leaf nodes’. These non leaf nodes can then be combined and hashed, until all the data blocks can be represent by a single root hash. Here’s an easier way to conceptualize it:

![](https://cdn-images-1.medium.com/freeze/max/60/0*aStXJqYfNcFgn-j1.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*aStXJqYfNcFgn-j1.)

A DAG is a way to model topological sequences of information that have no cycles. A simple example of a DAG is a family tree. A merkle DAG is basically a data structure where hashes are used to reference data blocks and objects in a DAG. This creates several useful features: all content on IPFS can be uniquely identified, since each data block has a unique hash. Plus the data is tamper-resistant because to alter it would change the hash, as shown below:

![](https://cdn-images-1.medium.com/freeze/max/60/0*AiVQ5qZOV2WcrHDJ.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*AiVQ5qZOV2WcrHDJ.)

Source: [ethereum.org](https://blog.ethereum.org/2014/02/18/ethereum-scalability-and-decentralization-updates/)

The central tenet of IPFS is modeling all data on a generalized merkle DAG. The significance of this security feature is hard to overstate. For comparison with client-server systems, see how this guy [hacked 40 websites in 7 minutes](https://hackernoon.com/how-i-hacked-40-websites-in-7-minutes-5b4c28bc8824).

**Version Control Systems**

Another powerful feature of the Merkle DAG structure is that it allows you to build a distributed version control system ([VCS](https://en.wikipedia.org/wiki/Distributed_version_control)). The most popular example of this is Github, which allows developers to easily collaborate on projects simultaneously. Files on Github are stored and versioned using a merkle DAG. It allows users to independently duplicate and edit multiple versions of a file, store these versions and later merge edits with the original file.

IPFS uses a similar model for data objects: as long as objects corresponding to the original data, and any new versions are accessible, the entire file history can be retrieved. Given that data blocks are stored locally across the network and can be cached indefinitely, this means that IPFS objects can be stored permanently.

Additionally, IPFS does not rely on access to Internet protocols. Data can be distributed in [overlay networks](https://en.wikipedia.org/wiki/Overlay_network), which are simply networks built on another network. These features are notable, because they are core elements in a censorship-resistant web. It could be a useful tool in promoting free speech to counter the prevalence of [internet censorship](http://www.visualcapitalist.com/internet-censorship-map/) around the world, but we should also be cognizant of the potential for abuse by bad actors.

**Self-certifying File System**

The last essential component of IPFS we’ll cover is the Self-certifying File System ([SFS](https://en.wikipedia.org/wiki/Self-certifying_File_System)). It is a distributed file system that doesn’t require special permissions for data exchange. It is “self-certifying” because data served to a client is authenticated by the file name (which is signed by the server). The result? You can securely access remote content with the transparency of local storage.

IPFS builds on this concept to create the InterPlanetary Name Space (IPNS). It is an SFS that uses [public-key cryptography](https://medium.com/@vrypan/explaining-public-key-cryptography-to-non-geeks-f0994b3c2d5) to self-certify objects published by users of the network. We mentioned earlier that all objects on IPFS can be uniquely identified, but this also extends to nodes. Each node on the network has a set of public keys, private keys and a node ID which is the hash of its public key. Nodes can therefore use their private keys to ‘sign’ any data objects they publish, and the authenticity of this data can be verified using the sender’s public key.

**Here’s a quick recap of the key IPFS components:**

*   With the Distributed Hash Table, nodes can store & share data without central coordination
*   IPNS allows exchanged data to be instantly pre-authenticated and verified using public key cryptography.
*   The Merkle DAG enables uniquely identified, tamper-resistant and permanently stored data
*   You can access past versions of edited data via the Version Control System

![](https://cdn-images-1.medium.com/freeze/max/60/0*erhuY4fEfd3PA4Im.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*erhuY4fEfd3PA4Im.)

Simple conceptual framework

**So why is all this important?**

IPFS provides high throughput, low latency, data distribution. It is also decentralized and secure. This opens up several interesting and exciting use cases. It can be used to deliver content to websites, globally store files with automatic versioning & backups, facilitate secure filesharing and encrypted communication.

Below are a few interesting projects being built on IPFS:

[Akasha](https://akasha.world/), _a Next-Generation social network_

[Balance3](https://www.balanc3.net/#/), _a triple-entry accounting platform_

[BlockFreight](https://blockfreight.com/), _an open network for global freight_

[Digix](https://digix.global/), _a platform for tokenizing physical gold_

[Infura](https://infura.io/), _an infrastructure provider for DApps_

[Livepeer](https://livepeer.org/), _a decentralized live-video streaming platform_

[Origin](https://www.originprotocol.com/en), _a peer-to-peer marketplace for the sharing economy_

[uPort](https://www.uport.me/), _a self-sovereign identity system_

The variety of these applications demonstrate the versatility of IPFS for several different use cases. It is also being used as a complementary file system for public blockchains and other p2p applications. At the time of writing it can cost several dollars to store a kilobyte of data in an Ethereum smart contract. This is a major constraint and there is currently massive growth in new decentralized apps (DApps) being launched. IPFS is interoperable with smart contracts and blockchain data, so it can add reliable, low-cost storage capacity to the ethereum ecosystem. The attempt to make Ethereum blockchain data natively accessible on IPFS is a separate protocol known as [IPLD](https://ipld.io/) (InterPlanetary Linked Data).

**Challenges**

Despite the impressive performance of IPFS, a few issues are yet to be fully resolved. Firstly, the content addressing on IPNS is currently not very user-friendly. Your typical IPNS link looks like this:

_ipfs.io/ipns/QmeQe5FTgMs8PNspzTQ3LRz1iMhdq9K34TQnsCP2jqt8wV/_

These links can be shortened to simpler names using a Domain Name System (DNS), but this introduces an external point-of-failure for content distribution. The content can however be still accessible through the original IPNS address. Some users also report that IPNS can be slow at resolving domain names, with delays of up to a few seconds. It’s not clear exactly what the root of this issue is.

_Update_ : _On 03/26/2018, IPNS released an upgrade with an experimental feature to speed up publishing/resolving. Details available_ [_here_](https://blog.ipfs.io/34-go-ipfs-0.4.14#ipns-improvements)

On IPFS there is also little incentive for nodes to maintain long term backups of data on the network. Nodes can choose to clear cached data to save space, meaning theoretically files can end up ‘disappearing’ over time if there are no remaining nodes hosting the data. At current adoption levels this isn’t a significant issue but in the long term, backing up large amounts of data requires strong economic incentives.

**Storage Markets**

Filecoin is a separate protocol designed to add economic incentives to file storage on IPFS, and foster a distributed storage market that rivals enterprise cloud storage (like Amazon S3, etc). Instead of centralized infrastructure with fixed pricing, IPFS + FileCoin offers storage on a global network of local providers who have the freedom to set prices based on supply and demand. Instead of a [Proof-of-Work](https://en.wikipedia.org/wiki/Proof-of-work_system) consensus algorithm like Bitcoin, Filecoin uses [Proof-of-Storage](https://filecoin.io/filecoin.pdf) to ensure security and reliability. So anyone can join the network, offer unused hard drive space on their computing device, and get rewarded in Filecoin tokens for data storage and retrieval services.

The network is being developed on Ethereum, so smart contract integration could produce advanced features like escrow, insurance, etc in the storage marketplace. In theory this economic model should develop a highly competitive free market with potentially lower costs than large-scale providers. But FileCoin has not been launched yet, so it will be interesting to observe how these concepts play out in reality.

**Getting Started**

IPFS is a highly ambitious endeavor, and obviously the precise mechanics of how the system functions are far more complex than what has been described in this guide. We’ll leave those details for the cryptographers and computer scientists to enjoy. You don’t have to be an expert to _use_ IPFS, so if any of the advantages or use cases seem useful or appealing to you, download IPFS & get started [here](https://ipfs.io/docs/getting-started/). If you’ve got gigabytes or terabytes of unused storage and would like to make good use of that idling capacity, you can [sign up](https://docs.google.com/forms/d/e/1FAIpQLSfdFpWhJj8OIGA2iXrT3bnLgVK9bgR_1iLMPdAcXLxr_1d-pw/viewform?c=0&w=1) to be an early Filecoin miner when the network launches. You can also [sign up](https://docs.google.com/forms/d/e/1FAIpQLSdCOjMenUU7WtT54zeAivCS2nnaWYQIgaXh0eRdIdpi6Pwkew/viewform) if you’re interested in being an early storage user.

Using IPFS is quite remarkable and understanding the technical wizardry that makes it possible is even more exciting. If successful, IPFS and its complementary protocols could provide resilient infrastructure for the next generation of the web. The web that was promised to be distributed, secure, & transparent.

* * *

_Sources_

Comer, Douglas. _Computer networks and internets_. Pearson, 2015. [goo.gl/AbM8st](http://goo.gl/AbM8st)

IPFS whitepaper (draft 3) [http://goo.gl/zwKD9J](http://goo.gl/zwKD9J)

Filecoin whitepaper [https://goo.gl/RrxcvX](https://goo.gl/RrxcvX)