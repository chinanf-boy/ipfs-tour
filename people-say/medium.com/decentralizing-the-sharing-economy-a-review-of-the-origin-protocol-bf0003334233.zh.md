
-   `author:` <https://medium.com/@merunasgrincalaitis?source=post_header_lockup>
-   `url:` <https://medium.com/@merunasgrincalaitis/how-to-host-your-ipfs-files-online-forever-f0c56b9b5398>

* * *

<details>

<summary> 目录 </summary>

<!-- START doctoc -->

<!-- END doctoc -->

</details>

# 如何永久在线托管您的IPFS文件

**TL; DR;**

在服务器上安装IPFS,使用创建新的repo`ipfs init`. 使用以下命令启动后台IPFS节点守护程序进程: `ipfs daemon &`,将文件添加到网络中`ipfs add -r <your-files>`并固定你想永远在线的哈希值`ipfs pin add -r <your-ipfs-hash/>`. 确保您的服务器正在运行节点进程. 

* * *

你有没有想过如何永久保持你的IPFS文件在线?如果你在某个时候使用过IPFS,你可能已经看到你的文件在24小时后消失了. 

在本教程中,我将向您展示如何保持文件在线,只要您有一台服务器并且您的内容已固定. 

IPFS是托管下放文件的绝佳平台,无需担心Ddos攻击和服务器问题. 它只是工作,它是静态网站的理想选择. 

想要完全下放的Dapps. 

问题是,一旦你将文件添加到网络,如果没有其他人固定它,它会在大约24小时后消失. 它被网络收集垃圾. 

因此,如果您使用以下命令在IPFS上托管网站: 

ipfs add -r my-website-files /

您的网站将在返回的哈希值上联机,但如果您不使用自己的IPFS节点将其保持在线状态,它将在24小时后关闭. 

因此,为了避免这种情况并保持文件存活,我将向您展示3个简单步骤来创建自己的IPFS节点以维护这些文件: 

### 1. 获取托管服务器

首先,你需要一台服务器. 在我的情况下,我在amazon AWS中有一个ubuntu实例和他们的免费年份. 

只需在他们的页面中注册并免费启动一个ubuntu服务器. 这是一个简单的4分钟教程: <https://www.youtube.com/watch?v=OTCwx1hjA24>

### 2. 在Ubuntu服务器上安装IPFS

从官方页面下载安装IPFS: <https://ipfs.io/docs/install/>

![](https://cdn-images-1.medium.com/freeze/max/60/1*uv6GieROl46tHww_N8xJ_Q.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*uv6GieROl46tHww_N8xJ_Q.png)

在我的情况下,我会选择选项`amd64`这是ubitntu的64位版本. 该`386`linux binary适用于32位版本. 

连接到您的ubuntu实例并从终端下载: 

wget的<https://dist.ipfs.io/go-ipfs/v0.4.10/go-ipfs_v0.4.10_linux-amd64.tar.gz>

然后使用以下命令解压缩文件: 

    tar -xvzf 

删除下载的文件: `rm go-ipfs_v0.4.10_linux-amd64.tar.gz`并通过执行install.sh文件来安装它: 

cd go-ipfs && sudo ./install.sh

然后执行`ipfs`确保它的财产安装并删除安装文件夹`rm -r go-ipfs/`. 

### 3. 启动IPFS节点并固定要保持联机的文件

1.  首先创建一个存储库,用于IPFS为您的系统创建必要的配置文件`ipfs init`

2\. 现在启动一个守护进程,这是一个IPFS节点,它将与网络的其余部分进行通信,这是在线交换和上传文件所需的: 

ipfs守护进程&

这将在后台创建一个节点. 

您可以使用CTRL + C随时退出下一条消息,因为该节点现在是后台进程. 

如果要停止后台进程,只需键入即可`fg` (前景) 将该进程带到前台并使用CTRL + C将其停止. 

3\. 然后获取要在IPFS上托管的文件. 我将从git获取我的网站文件: 

git clone<git-repo>

4\. 现在将文件添加到网络: 

ipfs add -r<my-files>

在我的情况下它是: `ipfs add -r dapp-transactions/`

五. 最后,为了保持文件在线并避免它们被垃圾收集,只需使用`pin`命令,只要您的守护程序正在运行,它们将保持在线状态. 它们不会被垃圾收集: 

ipfs pin add -r<your-files>

就我而言,它是`ipfs pin add -r QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF/`

![](https://cdn-images-1.medium.com/freeze/max/60/1*f-piNIMg0HtpH2o5_igWOA.gif?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*f-piNIMg0HtpH2o5_igWOA.gif)

* * *

而已!您添加和固定的文件将永远在线,您可以从返回的哈希中访问它们. 在我的情况下它是: `QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF`

所以要访问它我会去`https://gateway.ipfs.io/ipfs/<file-hash>`

就我而言,它是<https://gateway.ipfs.io/ipfs/QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF>

* * *

现在,只要您有一个服务器节点或其他节点固定内容,您就知道如何将分散的文件保持在线状态. 

除非您的文件受欢迎并且很多人将其从计算机中固定,否则您的文件将会死亡. 因此,最好通过本教程自行预防和存储. 

感谢您阅读整个教程!

如果您喜欢本教程,可以通过以下方式帮助我: 

-   给我一些鼓掌,每个人都喜欢拍手
-   分享文章并在媒体上关注我[Merunas Grincalaitis](https://medium.com/@merunasgrincalaitis)
-   在twitter上关注我@ merunas2我经常分享有趣的内容. 
-   如果您想聘请区块链开发人员,我可以帮助您创建一个惊人的Dapp. 看看我的github<https://github.com/merlox>
-   最后,感谢您来到这里并实际学习这些内容. 
