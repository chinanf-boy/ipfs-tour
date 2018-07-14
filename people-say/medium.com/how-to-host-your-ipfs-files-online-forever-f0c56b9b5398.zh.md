
-   `author:` <https://itnext.io/@mcchan1?source=post_header_lockup>
-   `url:` <https://itnext.io/build-a-simple-ethereum-interplanetary-file-system-ipfs-react-js-dapp-23ff4914ce4e>

* * *

<details>

<summary> 目录 </summary>

<!-- START doctoc -->

<!-- END doctoc -->

</details>

# 构建一个简单的以太坊+行星际文件系统 (IPFS) + React.js DApp. 

**我们为什么要建造这个?**

[*Click here to share this article on LinkedIn »*](https://www.linkedin.com/cws/share?url=https%3A%2F%2Fitnext.io%2Fbuild-a-simple-ethereum-interplanetary-file-system-ipfs-react-js-dapp-23ff4914ce4e)

**在以太坊区块链上存储大量数据是非常昂贵的**. 根据以太坊的黄纸,它是大约20,0000气体,256bit / 8字节 (1字) . 基于02/28/2018天然气价格为4 gwei / gas. 看到: <https://ethgasstation.info>目前的价格. 

每个交易8个字节20,000气体x 4 gwei / gas = 80,000 gwei,8个字节. 

8,000字节80,000 gwei. x 1000bytes / 8 = 10,000,000 gwei / kB = .01以太

.01以太网/ kB x 1000kB = 10以太网存储1Mb,价格为860美元/以太网= 8600.00美元!在以太坊区块链上存储1 GB文件需要花费8,600,000.00美元!

存储以太坊的38页PDF黄纸 (520Kb) = 4472美元. 看到: <http://eth-converter.com/>转换. 

如果我们只能在区块链上存储几Kb的数据,那么我们仍然需要依靠集中式服务器来存储数据. 值得庆幸的是,可以使用称为InterPlanetary文件系统 ("IPFS") 的分散网络上存储数据的解决方案. 看到: <https://ipfs.io/>阅读更多. 在IPFS中查找文件时,您要求网络查找将内容存储在唯一哈希后面的节点. 来自IPFS自己的网站: 

> "IPFS和Blockchain完美匹配!您可以使用IPFS处理大量数据,并将不可变的永久IPFS链接放入区块链事务中. 这个时间戳和保护您的内容,而不必将数据放在链本身上. "

**我们建造什么?**

一个简单的DApp,用于将文档上载到IPFS,然后将IPFS哈希存储在以太坊区块链上. 一旦IPFS哈希号被发送到以太坊区块链,用户将收到交易收据. 我们将使用Create-React-App框架来构建前端. 此Dapp适用于在浏览器中安装了MetaMask的任何用户. 

这就是我们完成后DApp的样子: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*BHlV4WFT04gxVQicSOgwCg.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*BHlV4WFT04gxVQicSOgwCg.png)

**如何建立它: **

注意: 请参阅我的github<https://github.com/mcchan1/eth-ipfs>如果你只是想要代码. 

在我们开始之前,这些是我做出的假设: 

**关于用户的假设: **用户安装了Metamask以与DApp交互. 

**关于你/开发人员的假设: **您对JavaScript和/或React.js以及Node.js / NPM有一定的了解. 重要说明: 请确保您运行的是当前版本的Node和NPM. 对于本教程,我正在运行: **节点v8.9.4**和**NPM 5.6.0**. 

**安装MetaMask. **如果还没有安装MetaMask,请转到<https://metamask.io/>并按照说明操作. 此DApp将假定用户已安装MetaMask. 

**创建一个目录来存储我们的DApp. **对于本教程,我将其称为"eth-ipfs". 

**使用NPM安装Create-React-App和其他依赖项. **使用NPM并安装以下内容: 

npm i create-react-app\
npm install react-bootstrap\
npm安装fs-extra\
npm install ipfs-api\
`npm install web3@^1.0.0-beta.26`

**输入"eth-ipfs"目录,输入"npm start"**和Create-React-App应该自动渲染<http://localhost:3000/>. 

*注意: 如果您到目前为止尚未使用create-react-app,则可能必须先在全局安装它*

*1. sudo npm install -g create-react-app\
或者npm install -g create-react-app*

*2. create-react-app eth-ipfs*

*3. cd进入eth-ipfs和"npm start"*

**在Rinkeby testnet上使用Remix部署以下Solidity代码. **看到,<https://remix.ethereum.org>. 你需要一些Rinkeby测试以太,如果你还没有一些Rinkeby龙头免费测试以太. <https://www.rinkeby.io/#faucet>. 

pragma solidity ^ 0.4.17;

合同合同{\
string ipfsHash;

function sendHash (string x) public {\
ipfsHash = x;\
}

function getHash () public view returns (string x) {\
return ipfsHash;\
}

}

**保存部署它的合同地址和应用程序二进制接口 (ABI) . **要获得合同的ABI,请在Remix中转到您的合同地址: 

单击"编译"选项卡,然后单击灰色的"详细信息"按钮. 

![](https://cdn-images-1.medium.com/freeze/max/60/1*QDTRyuLk6zK6ZMFWgc47Yw.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*QDTRyuLk6zK6ZMFWgc47Yw.png)

这将打开Details窗口. 复制"ABI",它是一个JSON文件. 

![](https://cdn-images-1.medium.com/freeze/max/60/1*RpCmf2eLsgS7ppkE-Gy3sQ.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*RpCmf2eLsgS7ppkE-Gy3sQ.png)

我个人更喜欢将ABI JSON放入格式化程序中,例如<https://jsonformatter.org>并在我的javascript代码中使用它之前检查它是否有效. 保存合同地址和ABI以供日后使用. 

在我们的"eth-ipfs / src"目录中,创建以下文件: **web3.js**,**ipfs.js**,和**storehash.js**. 我们的大部分代码都将在**App.js**. 

![](https://cdn-images-1.medium.com/freeze/max/60/1*ofqwUkZCSWHPhy0hJlv2-g.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*ofqwUkZCSWHPhy0hJlv2-g.png)

**web3.js**

我们想使用1.0版本的web3.js,因为与0.20版本不同,1.0允许我们在我们的javascript中使用async并等待而不是promises. 目前,MetaMask的默认web3.js提供程序是0.20版本. 所以,让我们确保我们覆盖Metamask的web3版本0.20的默认版本,并使用我们的1.0. 这是代码: 

//为我们的1.0版本覆盖metamask v0.2. \
//1.0让我们使用async并等待而不是promises

从'web3'导入Web3;

const web3 = new Web3 (window.web3.currentProvider) ;

导出默认web3;

**storehash.js**

为了让web3.js能够访问我们之前部署到以太坊的Rinkeby testnet的合同,您需要以下内容: 1) 合同地址和2) 合同中的ABI. 一定要从/ src目录中导入web3.js文件. 这是代码: 

从'./web3'导入web3;

//访问我们的本地副本到在rinkeby testnet上部署的合同\
//使用您自己的合同地址

const address ='0xb84b12e953f5bcf01b05f926728e855f2d4a67a9';

//使用合同中的ABI

const abi =\[\
{\
"常数": 是的,\
"输入": \[],\
"名字": "getHash",\
"输出": \[\
{\
"名字": "x",\
"type": "string"\
}\
    ],\
"应付": 虚假,\
"stateMutability": "查看",\
"type": "function"\
},\
{\
"常数": 错误,\
"输入": \[\
{\
"名字": "x",\
"type": "string"\
}\
    ],\
"name": "sendHash",\
"输出": \[],\
"应付": 虚假,\
"stateMutability": "无偿",\
"type": "function"\
}\
]

export default new web3.eth.Contract (abi,address) ;

**ipfs.js**

在本教程中,我们将运行[ipfs.infura.io](http://ipfs.infura.io)节点连接到IPFS而不是在我们自己的计算机上运行IPFS守护程序. 在代码注释中,如果将IPFS安装为全局依赖项,则还可以选择运行自己的IPFS守护程序. 看到,<https://infura.io/>有关使用其节点的更多信息. 这是代码: 

//使用infura.io节点,否则ipfs要求您在自己的计算机/服务器上运行//守护程序. 

const IPFS = require ('ipfs-api') ;\
const ipfs = new IPFS ({host: 'ipfs.infura.io',port: 5001,protocol: 'https'}) ;

//使用本地守护进程运行\
// const ipfsApi = require ('ipfs-api') ;\
// const ipfs = new ipfsApi ('localhost','5001',{protocol: 'http'}) ;

export default ipfs;

**App.js**

这是App.js中的操作顺序

1.  设置状态变量. 
2.  捕获用户的文件. 
3.  将文件转换为缓冲区. 
4.  将缓冲的文件发送到IPFS
5.  IPFS返回一个哈希值. 
6.  获取用户的MetaMask以太坊地址
7.  发送IPFS以便在以太坊上存储. 
8.  使用MetaMask,用户将确认交易到以太坊. 
9.  以太坊合约将返回一个交易哈希数. 
10. 交易哈希值可用于生成具有诸如所使用的气体量和块编号之类的信息的交易收据. 
11. IPFS和以太坊信息将在使用Bootstrap for CSS的表中呈现. 注意: 我没有创建一个isLoading类型变量来自动重新呈现blockNumber和gasUsed变量的状态. 因此,现在,您必须再次单击或实现自己的加载图标. 描述变量和函数的表,后面是代码本身如下: 

![](https://cdn-images-1.medium.com/freeze/max/60/1*_wCKVcaT_MHmVWk1MLFxZQ.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*_wCKVcaT_MHmVWk1MLFxZQ.png)

![](https://cdn-images-1.medium.com/freeze/max/60/1*M37jYzn2vHxSKU2Be20LVA.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*M37jYzn2vHxSKU2Be20LVA.png)

![](https://cdn-images-1.medium.com/freeze/max/60/1*BwOHqXWx6kx7wspCyPBcPA.png?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*BwOHqXWx6kx7wspCyPBcPA.png)

最后,这是**App.js**码: 

从'react'导入React,{Component};\
//从'./logo.svg'导入徽标;\
import'./App.css';\
从'./web3'导入web3;\
从'./ipfs'导入ipfs;\
从'./storehash'导入storehash;

class App扩展Component {

    state = {  
      ipfsHash:null,  
      buffer:'',  
      ethAddress:'',  
      blockNumber:'',  
      transactionHash:'',  
      gasUsed:'',  
      txReceipt: ''     
    };

captureFile = (event) => {\
event.stopPropagation () \
event.preventDefault () \
const file = event.target.files\[0]\
让reader = new window.FileReader () \
reader.readAsArrayBuffer (文件) \
reader.onloadend = () => this.convertToBuffer (读者) \
};\
convertToBuffer = async (reader) => {\
//文件转换为缓冲区以上传到IPFS\
const buffer = await Buffer.from (reader.result) ;\
//设置此缓冲区 - 使用es6语法\
this.setState ({缓冲器}) ;\
};

onClick = async () => {

尝试{\
this.setState ({blockNumber:  "等待.."}) ;\
this.setState ({gasUsed:  "等待..."}) ;

//点击控制台获取交易收据\
//看到: <https://web3js.readthedocs.io/en/1.0/web3-eth.html#gettransactionreceipt>

等待web3.eth.getTransactionReceipt (this.state.transactionHash, (err,txReceipt) => {\
的console.log (ERR,txReceipt) ;\
this.setState ({txReceipt}) ;\
}) ;//等待getTransactionReceipt

等待this.setState ({blockNumber: this.state.txReceipt.blockNumber}) ;\
等待this.setState ({gasUsed: this.state.txReceipt.gasUsed}) ;\
} //试试\
赶上 (错误) {\
的console.log (误差) ;\
} //抓住\
} // onClick

onSubmit = async (event) => {\
event.preventDefault () ;

     //bring in user's metamask account address  
      const accounts = await web3.eth.getAccounts();  
       
      console.log('Sending from Metamask account: ' + accounts\[0\]);

    //obtain contract address from storehash.js  
      const ethAddress= await storehash.options.address;  
      this.setState({ethAddress});

    //save document to IPFS,return its hash#, and set hash# to state  
    //[https://github.com/ipfs/interface-ipfs-core/blob/master/SPEC/FILES.md#add](https://github.com/ipfs/interface-ipfs-core/blob/master/SPEC/FILES.md#add) 

      await ipfs.add(this.state.buffer, (err, ipfsHash) => {  
        console.log(err,ipfsHash);  
        //setState by setting ipfsHash to ipfsHash\[0\].hash   
        this.setState({ ipfsHash:ipfsHash\[0\].hash });

//将以太坊合约方法"sendHash"和.send IPFS哈希调用到etheruem合约\
//从以太坊合约中返回事务哈希\
//看,这个<https://web3js.readthedocs.io/en/1.0/web3-eth-contract.html#methods-mymethod-send>  

        storehash.methods.sendHash(this.state.ipfsHash).send({  
          from: accounts\[0\]   
        }, (error, transactionHash) => {  
          console.log(transactionHash);  
          this.setState({transactionHash});  
        }); //storehash   
      }) //await ipfs.add   
    }; //onSubmit

render () {

      return (  
        <div className="App">  
          <header className="App-header">  
            <h1> Ethereum and IPFS with Create React App</h1>  
          </header>  
            
          <hr />

<Grid>  
          <h3> Choose file to send to IPFS </h3>  
          <Form onSubmit={this.onSubmit}>  
            <input   
              type = "file"  
              onChange = {this.captureFile}  
            />  
             <Button   
             bsStyle="primary"   
             type="submit">   
             Send it   
             </Button>  
          </Form>

<hr/>  
 <Button onClick = {this.onClick}> Get Transaction Receipt </Button>

  <Table bordered responsive>  
                <thead>  
                  <tr>  
                    <th>Tx Receipt Category</th>  
                    <th>Values</th>  
                  </tr>  
                </thead>  
                 
                <tbody>  
                  <tr>  
                    <td>IPFS Hash # stored on Eth Contract</td>  
                    <td>{this.state.ipfsHash}</td>  
                  </tr>  
                  <tr>  
                    <td>Ethereum Contract Address</td>  
                    <td>{this.state.ethAddress}</td>  
                  </tr>

                  <tr>  
                    <td>Tx Hash # </td>  
                    <td>{this.state.transactionHash}</td>  
                  </tr>

                  <tr>  
                    <td>Block Number # </td>  
                    <td>{this.state.blockNumber}</td>  
                  </tr>

                  <tr>  
                    <td>Gas Used</td>  
                    <td>{this.state.gasUsed}</td>  
                  </tr>  
                  
                </tbody>  
            </Table>  
        </Grid>  
     </div>  
      );  
    } //render  

} //应用

导出默认App;

我在src /中添加了一点CSS**App.css**使眼睛更容易: 

/\*我添加了一些css\*/\
输入\[类型="文件"]{\
display: inline-block;\
}

.table {\
最大宽度: 90%;\
保证金: 10px;\
}\
.table th {\
text-align: center;\
}\
/\*我的css结束了\*/

并添加一些导入**SRC / index.js**: 

/*<https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#adding-a-stylesheet>*/\
import'bootstrap / dist / css / bootstrap.css';\
import'bootstrap / dist / css / bootstrap-theme.css';

这就对了!你的DApp应该完成. 所以你需要做的就是选择一个文件,发送它,并获得一个交易收据. 如果您通过localhost: 3000连接到IPFS节点,那么您应该能够在其中一个IPFS网关上看到您的文件. [https://gateway.ipfs.io/ipfs/](https://gateway.ipfs.io/ipfs/QmYjh5NsDc6LwU3394NbB42WpQbGVsueVSBmod5WACvpte) +你的IPFS哈希#. 

例如: <https://gateway.ipfs.io/ipfs/QmYjh5NsDc6LwU3394NbB42WpQbGVsueVSBmod5WACvpte>

关于IPFS的一个注意事项是,除非您的文件被另一个节点接收或者您将其固定,否则IPFS最终将垃圾收集您的文件. 他们的网站上有很多关于此的内容. 

**参考链接: **

-   <https://ipfs.io/docs/getting-started/>
-   <https://web3js.readthedocs.io/en/1.0/index.html>
-   <https://infura.io/>
-   <https://react-bootstrap.github.io/getting-started/introduction>
-   <https://metamask.io/>
-   <https://github.com/ipfs/js-ipfs-api>
-   <https://remix.ethereum.org/>
-   <https://ethereum.github.io/yellowpaper/paper.pdf>
-   <https://ethgasstation.info>
-   <http://eth-converter.com/>
-   <https://www.rinkeby.io/#faucet>
-   <https://developer.mozilla.org/en-US/docs/Web/API/FileReader>
-   <https://github.com/ipfs/interface-ipfs-core/blob/master/SPEC/FILES.md#add>
-   <https://web3js.readthedocs.io/en/1.0/web3-eth-contract.html#methods-mymethod-send>
-   <https://web3js.readthedocs.io/en/1.0/web3-eth.html#gettransactionreceipt>
-   <https://github.com/mcchan1/eth-ipfs>
