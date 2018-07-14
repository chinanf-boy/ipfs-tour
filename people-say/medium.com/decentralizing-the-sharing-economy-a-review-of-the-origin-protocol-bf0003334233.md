- `author:` https://medium.com/@merunasgrincalaitis?source=post_header_lockup
- `url:` https://medium.com/@merunasgrincalaitis/how-to-host-your-ipfs-files-online-forever-f0c56b9b5398

---

<details>

<summary> 目录 </summary>

<!-- START doctoc -->
<!-- END doctoc -->


</details>

How to Host Your IPFS Files Online Forever
==========================================

**TL;DR;**

Install IPFS on a server, create a new repo with `ipfs init` . Start a background IPFS node daemon process with: `ipfs daemon &` , add the files to the network with `ipfs add -r <your-files>` and pin the hash that you want to keep online forever with `ipfs pin add -r <your-ipfs-hash/>` . Make sure that your server has the node process running.

* * *

Have you ever wondered how to keep your IPFS files online forever? If you’ve used IPFS at some point, you‘ve probably have seen that your files just dissapear after 24 hours or so.

In this tutorial I’ll show you how to keep your files online as long as you have a server and your content is pinned.

IPFS is a fantastic platform for hosting descentralized files without worrying about Ddos attacks and server problems. It just works and it’s ideal for static websites.

Dapps that you want to be fully descentralized.

The problem is that once you add a file to the network, it dissapears after about 24 hours if nobody else has it pinned. It gets garbage collected by the network.

So if you host a website on IPFS with the command:

ipfs add -r my-website-files/

Your website will be online on the hash returned but it will go down after 24 hours if you don’t keep it online with your own IPFS node.

So in order to avoid that and keep the files alive, I’ll show you 3 simple steps to create your own IPFS node in order to maintain those files:

### 1\. Get a hosting server

First you’ll need a server. In my case I have a ubuntu instance in amazon AWS with their free year.

Simply sign up in their page and start an ubuntu server for free. Here’s a simple 4 minute tutorial to do that: [https://www.youtube.com/watch?v=OTCwx1hjA24](https://www.youtube.com/watch?v=OTCwx1hjA24)

### 2\. Install IPFS on the Ubuntu Server

Install IPFS by downloading it from their official page: [https://ipfs.io/docs/install/](https://ipfs.io/docs/install/)

![](https://cdn-images-1.medium.com/freeze/max/60/1*uv6GieROl46tHww_N8xJ_Q.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*uv6GieROl46tHww_N8xJ_Q.png)

In my case I’ll select the option `amd64` which is for the 64 bits version of ubuntu. The `386` linux binary is for the 32 bits version.

Connect to your ubuntu instance and download it from the terminal:

wget [https://dist.ipfs.io/go-ipfs/v0.4.10/go-ipfs\_v0.4.10\_linux-amd64.tar.gz](https://dist.ipfs.io/go-ipfs/v0.4.10/go-ipfs_v0.4.10_linux-amd64.tar.gz)

Then extract the file with the command:

    tar -xvzf 

Remove the downloaded file with: `rm go-ipfs_v0.4.10_linux-amd64.tar.gz`and install it by executing the install.sh file with:

cd go-ipfs && sudo ./install.sh

Then execute `ipfs` to ensure that it’s propertly installed and remove the installation folder with `rm -r go-ipfs/` .

### 3\. Start an IPFS node & pin the files that you want to keep online

1.  First create a repository that will be used for IPFS to create the necessary configuration files for your system with `ipfs init`

2\. Now start a daemon process which is an IPFS node that will communicate with the rest of the network, required to exchange and upload files online:

ipfs daemon &

This will create a node in the background.

You can exit that next message anytime with CTRL + C because the node is now a background process.

If you want to stop the background process just type`fg` (foreground) to bring that process to the foreground and stop it with CTRL + C.

3\. Then get the files that you want to host on IPFS. I’ll get my website files from git with:

git clone <git-repo>

4\. Now add the files to the network with:

ipfs add -r <my-files>

In my case it is: `ipfs add -r dapp-transactions/`

5\. Finally, to keep the files online and avoid them to be garbage collected, just use the`pin` command and they will remain online as long as your daemon is running. They won’t be garbage collected:

ipfs pin add -r <your-files>

In my case it’s `ipfs pin add -r QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF/`

![](https://cdn-images-1.medium.com/freeze/max/60/1*f-piNIMg0HtpH2o5_igWOA.gif?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*f-piNIMg0HtpH2o5_igWOA.gif)

* * *

That’s it! The files that you added and pinned will be online forever and you can access them from the hash returned. In my case it’s: `QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF`

So to access it I’ll just go to `https://gateway.ipfs.io/ipfs/<file-hash>`

In my case it’s [https://gateway.ipfs.io/ipfs/QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF](https://gateway.ipfs.io/ipfs/QmNqFpK2X8indC6H2zjdzRG6PHx7C3iRMeTpFBsVHAMLVF)

* * *

Now you know how to keep your descentralized files online as long as you have a server node or other nodes pinning your content.

Unless your file gets popular and a lot of people pin it from their computer, your file will die. So better be prevented and store it yourself with this tutorial.

Thank you for reading the entire tutorial!

If you liked this tutorial you can help me in the following ways:

*   Give me some claps, everybody loves claps
*   Share the article and follow me on medium [Merunas Grincalaitis](https://medium.com/@merunasgrincalaitis)
*   Follow me on twitter @merunas2 I usually share interesting content.
*   If you want to hire a blockchain developer, I may help you create an amazing Dapp. Take a look at my github [https://github.com/merlox](https://github.com/merlox)
*   Finally thank you for being here and actually learning from this content.