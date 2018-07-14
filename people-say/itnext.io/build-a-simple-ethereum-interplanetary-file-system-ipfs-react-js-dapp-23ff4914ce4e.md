- `author:` https://medium.com/@kojoaddaquay?source=post_header_lockup
- `url:` https://medium.com/@kojoaddaquay/decentralizing-the-sharing-economy-a-review-of-the-origin-protocol-bf0003334233

---


<details>

<summary> 目录 </summary>

<!-- START doctoc -->
<!-- END doctoc -->


</details>

Decentralizing the Sharing Economy: A Review of the Origin Protocol
===================================================================

For most of human history, economic exchange has largely been peer-to-peer (P2P). Activities like lending money, sharing accommodation, and providing skilled services occurred within the boundaries of social trust and community relations. However this economic structure was largely diminished after the Industrial Revolution and subsequent emergence of large corporations. Over the last two centuries mass production and distribution shaped the economic landscape, creating a global abundance of economic, intellectual & physical resources.

![](https://cdn-images-1.medium.com/freeze/max/60/0*Eicy2kUzuWuUlyAZ.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*Eicy2kUzuWuUlyAZ.)

Example of p2p exchange: banana for scale. Source: [imgur](http://i.imgur.com/Zcwaz3n.jpg)

Historically, this is a blink of an eye and the development of the internet in the 90’s brought us the first major resurgence in P2P commerce, finally enabling our abundant resources to be exchanged between individuals en masse. Web services like eBay and Craigslist were the pioneering platforms of this revitalized form of commerce. Over the last decade, the convergence of advanced mobile technology and location-based services has enabled this socioeconomic phenomena to expand beyond the simple exchange of goods, to the fractional usage of assets. Examples are on-demand services like AirBnb, Lyft, and TaskRabbit, familiarly known as the ‘sharing economy’. The untapped potential market is about $2 trillion globally, while the current market is around [$250bn](https://www.brookings.edu/wp-content/uploads/2016/12/sharingeconomy_032017final.pdf).

The four main functionalities of P2P commerce are identity, listings, payments, and scheduling. Existing online platforms have several weaknesses in these domains that can be improved by decentralized technologies. Currently, users have to create an account for each platform, and user data is siloed across several companies. Listings are also exclusive to individual platforms, and there is typically unfair value capture during payments. Fees charged to buyers and sellers can capture up to 30% of the value of each transaction, and there are often no better alternatives for users in markets where a single entity has the largest community of buyers and sellers such as Airbnb. This value capture will be as much as [$40bn](https://www.juniperresearch.com/resources/infographics/sharing-economy-market-snapshot-2017) annually by 2022.

### Origin Protocol

Origin is a an open-source protocol, that proposes a radically new way of facilitating the exchange of fractional usage assets. A key value proposition is to open-source the main functionalities of third-party intermediaries for several different market verticals. Anyone can use the Origin infrastructure to deploy product-specific applications (like art, cosmetics, office space) and target regional or global markets. By eliminating the high capital costs of building proprietary technology, innovators and entrepreneurs will gain a more level playing field against industry incumbents. This would enable competing marketplaces and participants, which over time will likely reduce transaction costs and improve user experiences. Additionally, this [franchising strategy](https://multicoin.capital/2017/10/24/crypto-franchising-new-old/) will be a key driver for cost-effective user growth and innovation within the ecosystem.

Another key value proposition Origin offers is identity management and privacy. Users will be able to self-manage a verified digital identity through 3rd party applications like [uPort](https://www.uport.me/). This identity can then be used to transact across different markets on the platform. Users can also transact pseudonymously with the consent of sellers. This configuration puts users in complete control over their data.

![](https://cdn-images-1.medium.com/freeze/max/60/0*dLJNmYk3jWSFbVok.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*dLJNmYk3jWSFbVok.)

Source: Origin Product Brief

The Origin protocol consists of the following parts:

**1\. Origin decentralized app (DApp)**

The DApp will be the front end where users create, manage, validate and publish listings. It aims to ultimately serve as a central hub to access all listings, as other 3rd party apps will be able to adopt similar functionalities for specific use cases.

**2\. Shared data layer**

The shared data layer will utilize the Ethereum blockchain to establish digital identities for users, execute smart contracts, record transactions on an immutable ledger, and store critical transactional data such as pricing. Front-end meta data like images and descriptions are currently expensive to store on the blockchain, so will be stored on the [Interplanetary File System](https://medium.com/@ConsenSys/an-introduction-to-ipfs-9bba4860abd0) (IPFS); a distributed file system. Data stored on the IPFS will have a unique content hash, and this hash will be stored on the Ethereum blockchain. This design choice efficiently minimizes storage and computing costs on chain, while preserving the security of data off chain. It will also improve scalability of the platform for mainstream adoption.

**3\. Smart contracts**

Each listing will have a set of smart contracts that will be used to publish or manage listings, confirm bookings, and facilitate other interactions between buyers and sellers.

**4\. Listing indexing server**

This is the bridge between data stored on the Ethereum blockchain and content stored on the IPFS. The server continuously identifies content hashes from the smart contract and retrieves the listings on the IPFS, which are then indexed. The indexing enables the DApp to conduct basic search and filtering of listings.

### Protocol Mechanics

The following steps briefly outline how buyers and sellers interact with the platform, and how it facilitates exchange.

**Seller**

1.  Creates listing on Origin enabled DApp
2.  DApp validates listing and publishes to IPFS
3.  IPFS publishes listing and returns content hash
4.  DApp sends content hash to Ethereum smart contract, and receives Ethereum transaction ID
5.  DApp monitors pending Ethereum transaction and notifies seller if submission is successful.

**Buyer**

1.  Connects to Origin DApp to search for listings.
2.  Indexing server requests content, and a smart contract returns IPFS content hashes.
3.  Indexing server returns listings, which can be filtered and browsed by buyer on DApp.
4.  Buyer selects desired listing and usage interval
5.  DApp checks with a set of oracles for fair exchange rate and sends booking request to a smart contract.
6.  Smart contract verifies with a set of oracles, and confirms booking if correct amount it sent and usage interval is valid.

### Tokenomics

The Origin token will be an [ERC20](https://hackernoon.com/erc20-tokens-b3b50c95ad08) token, which will be the settlement currency for all transactions on the platform. To avoid confusion and promote mainstream adoption, Origin aims to eventually enable users to transact in their preferred currency, including a fiat on-ramp.

3rd party marketplaces built on the platform can have their own tokens; an example is Origin’s partnership with [Beetoken](https://www.beetoken.com/), a P2P homesharing protocol. To learn more about how such applications will interact with the platform, I reached out to the team and got in touch with Coleman Maher, Head of Partnerships at Origin. Maher suggested that decentralized exchanges (DEX), atomic swaps or wallets may be utilized to integrate applications with separate tokens.

While the use of the token as a settlement currency could add value to the token under substantial user growth and high transaction volume, ultimately this is not enough for it to act as a reliable store of value over time. If the platform reaches successful mainstream adoption, the significance of the Origin token potentially lies in the staking mechanisms built into the arbitration and reputation systems.

**Arbitration**

Origin employs the Deposit-Challenge-Vote system; this incentivizes good behavior on the platform (less fraud and spam), democratizes the handling of disputes, and is an effective way to maintain security and trust. It does this by requiring users to deposit an amount of Origin tokens during activities like publishing/booking a listing or filing a complaint. This amount will be held in escrow by smart contracts, so that in an incident such as a fraudulent post or improper use of a service, the staked tokens will be up for grabs in a community vote. Voters also stake tokens to participate in this trial by jury, and vote to support one party in the conflict. The party with the least votes, along with the minority of voters who sided with them will lose all their staked tokens. This conviction is facilitated by smart contracts, which then distribute those tokens to the winning party and majority voters. This system will likely reduce overall [token velocity](https://www.coindesk.com/blockchain-token-velocity-problem/) which can contribute to price appreciation.

**Reputation**

The primary means of gaining a high reputation on the platform is through positive reviews. A high reputation will provide users with several privileges: for example reputable sellers will be prioritized in searches, and reputable buyers could avoid minimum deposits.

Origin will enable users to boost their reputation on the platform by staking tokens. This offers a tangible value to holding Origin tokens; because as the network grows the value of these privileges will be higher, driving further demand for the token in a positive feedback loop. However, possible challenges down the road could be a concentration of wealth and benefits amongst early users and well-funded sellers. A severe degree of inequality could potentially distort markets. It is unclear how such developments will be addressed, however during my conversation with Maher he acknowledged the issue and said “..we are always thinking about the implications of different token incentives.”

Lastly, the tokens are intended to be used in the governance of the protocol. Any token holders (users, developers, investors) will be able to vote on proposals and govern the direction of business and software development. This adds further incentives to buying and holding the tokens.

### Mainstream adoption

To drive early adoption and user growth, Origin will implement a rewards program and referral bonuses. Users will earn small amounts of Origin tokens for participating in the ecosystem: activity such as creating listings, writing reviews, and verifying profiles will reward users. Users can also earn tokens by successfully drawing peers to the platform. The size of these rewards as a fraction of transaction volume will decrease over time, eventually to zero. The exact inflation rate is not yet available.

![](https://cdn-images-1.medium.com/freeze/max/60/0*_d839lwFKyqTnaOm.?q=20)

![](https://cdn-images-1.medium.com/max/1600/0*_d839lwFKyqTnaOm.)

Source: Origin Product Brief

There are several favorable demographic, economic, social, and technological trends that could help propel the Origin protocol towards a key role in the future sharing economy. 2 in 3 consumers worldwide are willing to share or rent their personal resources with others. People are preferring access over ownership, mostly because it is cheaper, more convenient, and makes good use of idling capacity. The environmental benefits of the sharing economy are difficult to quantify, but it is clear that sharing resources reduces material waste, and in many cases reduces greenhouse emissions. So it may be a key element in the systemic change necessary to alleviate the excessive pollution wreaked by industrialization.

Collaborative consumption is also a growing trend in both developed economies and emerging markets, and independent from any political or economic ideologies. This can be observed in the rapid growth of P2P commerce in both Europe and China. Millennials and Centennials are by far the largest demographic (~49%) participating in this new economy, which will be a key contributor to the growth in the next few decades. Millennials are currently leading consumer spending, purchasing over $1tn of goods & services annually. According to [Brookings](https://www.brookings.edu/wp-content/uploads/2016/12/sharingeconomy_032017final.pdf) the global sharing economy is currently expected to grow from $250bn to $335bn by 2025.

The Ethereum blockchain currently faces limitations in scalability, which was brought to light when Cryptokitties comedically congested the network. Scalability will also be a challenge for Origin; according to Maher some specific use cases may be more difficult to scale than others, such as real time ridesharing. However the protocol may benefit from technological breakthroughs that could alleviate scalability challenges, such as [Plasma, Raiden and sharding](https://blog.rexmls.com/sharding-raiden-plasma-the-scaling-solutions-that-will-unchain-ethereum-c590e994523b).

Origin is cofounded by Matthew Lui and Josh Fraser; both successful serial entrepreneurs with a track record of scaling successful products. They are building a talented team that will be integral to the development of the protocol in the growth stage. Being an open source protocol, Origin will be supported by a growing community of developers and entrepreneurs. The Origin Foundation is a non-profit entity dedicated to supporting the Origin protocol. The foundation plans to provide developer grants for large scale projects. It will also support innovators and entrepreneurs building on the platform.

“We aim to provide an SDK to make it easier for developers to make their own decentralized marketplaces with a smart contract library and easy to use APIs,” Maher said.

Many tenets of public blockchains, like disintermediation, censorship-resistance, transparency, and permissionless innovation resonate strongly with the ethos of the sharing economy. Both represent a fundamental departure from the economic paradigm of the last century, by redefining how human activity is organized. P2P commerce taps into the fabric of social interaction, with network effects that provide positive social and economic benefits for all involved. The Origin protocol lies at the intersection of blockchain technology and the sharing economy, so if successful it may provide the open-sourced infrastructure for the next generation of P2P commerce.

_Sources_

Sundararajan, Arun. _The sharing economy: The end of employment and the rise of crowd-based capitalism_. MIT Press, 2016. [goo.gl/3wGeG8](http://goo.gl/3wGeG8)

Liu, Matthew. Fraser, Joshua. Origin: The Sharing Economy Without Intermediaries. White Paper, version 0.3. [https://www.originprotocol.com/static/docs/whitepaper_v3.pdf](https://www.originprotocol.com/static/docs/whitepaper_v3.pdf)

Origin Product Brief [https://www.originprotocol.com/static/docs/product\_brief\_v17.pdf](https://www.originprotocol.com/static/docs/product_brief_v17.pdf)