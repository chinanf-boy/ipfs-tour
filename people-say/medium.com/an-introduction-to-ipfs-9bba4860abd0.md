- `author:` https://medium.com/@ConsenSys?source=post_header_lockup
- `url:` https://medium.com/@ConsenSys/an-introduction-to-ipfs-9bba4860abd0

---


<details>

<summary> 目录 </summary>

<!-- START doctoc -->
<!-- END doctoc -->


</details>

**An Introduction to IPFS**
===========================

![](https://cdn-images-1.medium.com/freeze/max/60/1*czZJ7mvEAqL4wNAg-jt9Ow.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*czZJ7mvEAqL4wNAg-jt9Ow.jpeg)

credit: Bogdan Burcea

“When you have [IPFS](https://ipfs.io/), you can start looking at everything else in one specific way and you realize that you can replace it all” — [Juan Benet](https://www.google.com/?gws_rd=ssl#q=juan+benet+ipfs)

#### A Less Technical Approach to IPFS

from John Lilic

This section will attempt to provide a high level insight as a prelude to my colleague, Dr. Christian Lundkvist’s, deep [dive technical summary](http://whatdoesthequantsay.com/2015/09/13/ipfs-introduction-by-example/) below.

IPFS began as an effort by Juan Benet to build a system that is very fast at moving around versioned scientific data. [Versioning](https://en.wikipedia.org/wiki/Software_versioning) gives you the ability to track how states of software change over time ([think Git](https://en.wikipedia.org/wiki/Git_%28software%29)). IPFS has since become thought of as the [The Distributed, Permanent Web](https://ipfs.io/ipfs/QmNhFJjGcMPqpuYfxL62VVB9528NXqDNMFXiqN5bgFYiZ1/its-time-for-the-permanent-web.html) ; “_IPFS is a distributed file system that seeks to connect all computing devices with the same system of files._ In some ways, this is similar to the original aims of the Web, but IPFS is actually more similar to a single bittorrent swarm exchanging git objects. IPFS could become a new major subsystem of the internet. If built right, it could complement or replace HTTP. It could complement or replace even more. It sounds crazy. It is crazy.”\[[1](https://ipfs.io/ipfs/QmNhFJjGcMPqpuYfxL62VVB9528NXqDNMFXiqN5bgFYiZ1/its-time-for-the-permanent-web.html)\]

At its core, IPFS is a versioned file system that can take files and manage them and also store them somewhere and then tracks versions over time. IPFS also accounts for how those files move across the network so it is also a distributed file system.

IPFS has rules as to how data and content move around on the network that are similar in nature to bittorrent. This file system layer offers very interesting properties such as:

\- websites that are completely distributed

\- websites that have no origin server

\- websites that can run entirely on client side browsers

\- websites that do not have any servers to talk to

**Content Addressing**

Instead of referring to objects (pics, articles, videos) by which server they are stored on, IPFS refers to everything by the hash on the file. The idea is that if in your browser you want to access a particular page then IPFS will ask the entire network “does anyone have this file that corresponds to this hash?” and a node on IPFS that does can return the file allowing you to access it.

IPFS uses content addressing at the HTTP layer. This is the practice of saying instead of creating an identifier that addresses things by location, we’re going to address it by some representation of the content itself. This means that the content is going to determine the address. The mechanism is to take a file, hash it cryptographically so you end up with a very small and secure representation of the file which ensures that someone can not just come up with another file that has the same hash and use that as the address. The address of a file in IPFS usually starts with a hash that identifies some root object and then a path walking down. Instead of a server, you are talking to a specific object and then you are looking at a path within that object.

**HTTP vs. IPFS to find and retrieve a file**

HTTP has a nice property where in the identifier is the location so it is easy to find the computers hosting the file and talk to them. This is useful and generally works very well but not in the offline case or in large distributed scenarios where you want to minimize load across the network.

In IPFS you separate the steps into two parts;

1.  Identify the file with content addressing
2.  Go and find it — when you have the hash then you ask the network you’re connected to ‘who has this content? (hash)’ and you connect to the corresponding nodes and download it.

The result is a peer to peer overlay that gives you very fast routing.

To learn more, watch the [Alpha Video](https://www.youtube.com/watch?v=8CMxDNuuAiQ).

#### IPFS by Example

from Dr. Christian Lundkvist

A technical Examination and [IPFS](http://ipfs.io/) (InterPlanetary File System) is a synthesis of well-tested internet technologies such as [DHTs](https://en.wikipedia.org/wiki/Distributed_hash_table), the [Git](https://git-scm.com/) versioning system and [Bittorrent](https://en.wikipedia.org/wiki/BitTorrent). It creates a P2P swarm that allows the exchange of _IPFS objects_. The totality of IPFS objects forms a cryptographically authenticated data structure known as a _Merkle DAG_ and this data structure can be used to model many other data structures. We will in this post introduce IPFS objects and the Merkle DAG and give examples of structures that can be modelled using IPFS.

**IPFS Objects**

[IPFS](http://ipfs.io/) is essentially a P2P system for retrieving and sharing _IPFS objects_. An IPFS object is a data structure with two fields:

*   _Data_ — a blob of unstructured binary data of size < 256 kB.
*   _Links_ — an array of Link structures. These are links to other IPFS objects.

A Link structure has three data fields:

*   _Name_ — the name of the Link.
*   _Hash_ — the hash of the linked IPFS object.
*   _Size_ — the cumulative size of the linked IPFS object, including following its links.

The _Size_ field is mainly used for optimizing the P2P networking and we’re going to mostly ignore it here, since conceptually it’s not needed for the logical structure.

IPFS objects are normally referred to by their Base58 encoded hash. For instance, let’s take a look at the IPFS object with hash _QmarHSr9aSNaPSR6G9KFPbuLV9aEqJfTk1y9B8pdwqK4Rq_ using the IPFS command-line tool (please try this at home!):

\> ipfs object get QmarHSr9aSNaPSR6G9KFPbuLV9aEqJfTk1y9B8pdwqK4Rq

{“Links”: \[{

“Name”: “AnotherName”,

“Hash”: “QmVtYjNij3KeyGmcgg7yVXWskLaBtov3UYL9pgcGK3MCWu”,

“Size”: 18},

{“Name”: “SomeName”,

“Hash”: “QmbUSy8HCn8J4TMDRRdxCbK2uCCtkQyZtY6XYv3y7kLgDC”,

“Size”: 58}\],

“Data”: “Hello World!”}

The reader may notice that all hashes begin with “Qm”. This is because the hash is in actuality a **multihash**, meaning that the hash itself specifies the hash function and length of the hash in the first two bytes of the multihash. In the examples above the first two bytes in hex is _1220_, where _12_ denotes that this is the SHA256 hash function and _20_ is the length of the hash in bytes — 32 bytes.

The data and named links gives the collection of IPFS objects the structure of a **Merkle DAG** — [DAG](https://en.wikipedia.org/wiki/Directed_acyclic_graph) meaning Directed Acyclic Graph, and [Merkle](https://en.wikipedia.org/wiki/Ralph_Merkle) to signify that this is a cryptographically authenticated data structure that uses cryptographic hashes to address content. It is left as an excercise to the reader to think about why it’s impossible to have cycles in this graph.

To visualize the graph structure we will visualize an IPFS object by a graph with Data in the node and the Links being directed graph edges to other IPFS objects, where the Name of the Link is a label on the graph edge. The example above is visualized as follows:

![](https://cdn-images-1.medium.com/freeze/max/60/1*9rVlSSzV0efkf18NiYo2eg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1200/1*9rVlSSzV0efkf18NiYo2eg.jpeg)

We will now give examples of various data structures that can be represented by IPFS objects.

#### **File systems**

IPFS can easily represent a file system consisting of files and directories

**Small Files**

A small file (< 256 kB) is represented by an IPFS object with _data_ being the file contents (plus a small header and footer) and no links, i.e. the _links_ array is empty. Note that the file name is not part of the IPFS object, so two files with different names and the same content will have the same IPFS object representation and hence the same hash.

We can add a small file to IPFS using the command _ipfs add_:

chris@chris-VBox:~/tmp$ ipfs add test_dir/hello.txt

added QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG test_dir/hello.txt

We can view the file contents of the above IPFS object using _ipfs cat_:

chris@chris-VBox:~/tmp$ ipfs cat QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG  
Hello World!

Viewing the underlying structure with _ipfs object_ get yields:

chris@chris-VBox:~/tmp$ ipfs object get QmfM2r8seH2GiRaC4esTjeraXEachRt8ZsSeGaWTPLyMoG

{“Links”: \[\],

“Data”: “\\u0008\\u0002\\u0012\\rHello World!\\n\\u0018\\r”}

We visualize this file as follows:

![](https://cdn-images-1.medium.com/freeze/max/60/1*dWuAv67ihETN3FAdzsb87A.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1200/1*dWuAv67ihETN3FAdzsb87A.jpeg)

**Large Files**

A large file (> 256 kB) is represented by a list of links to file chunks that are < 256 kB, and only minimal _Data_ specifying that this object represents a large file. The links to the file chunks have empty strings as names.

chris@chris-VBox:~/tmp$ ipfs add test_dir/bigfile.js

added QmR45FmbVVrixReBwJkhEKde2qwHYaQzGxu4ZoDeswuF9w test_dir/bigfile.js

chris@chris-VBox:~/tmp$ ipfs object get QmR45FmbVVrixReBwJkhEKde2qwHYaQzGxu4ZoDeswuF9w

{“Links”: \[{

“Name”: “”,

“Hash”: “QmYSK2JyM3RyDyB52caZCTKFR3HKniEcMnNJYdk8DQ6KKB”,

“Size”: 262158},  
{“Name”: “”,

“Hash”: “QmQeUqdjFmaxuJewStqCLUoKrR9khqb4Edw9TfRQQdfWz3”,

“Size”: 262158},

{“Name”: “”,

“Hash”: “Qma98bk1hjiRZDTmYmfiUXDj8hXXt7uGA5roU5mfUb3sVG”,

“Size”: 178947}\],

“Data”: “\\u0008\\u0002\\u0018* \\u0010 \\u0010 \\n”}

![](https://cdn-images-1.medium.com/freeze/max/60/1*bgKkxhSphiCdAF8QKm-oxw.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/1600/1*bgKkxhSphiCdAF8QKm-oxw.jpeg)

**Directory Structures**

A directory is represented by a list of links to IPFS objects representing files or other directories. The names of the links are the names of the files and directories. For instance, consider the following directory structure of the directory _test_dir_:

chris@chris-VBox:~/tmp$ ls -R test_dir  
test_dir:  
bigfile.js hello.txt my_dir  
test\_dir/my\_dir:  
my_file.txt testing.txt

The files _hello.txt_ and _my_file.txt_ both contain the string _Hello World!\\n_. The file _testing.txt_ contains the string _Testing 123\\n._

When representing this directory structure as an IPFS object it looks like this:

![](https://cdn-images-1.medium.com/freeze/max/60/1*-wVVj4B-YhxvF82iSUrbOQ.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*-wVVj4B-YhxvF82iSUrbOQ.jpeg)

Note the automatic deduplication of the file containing _Hello World!\\n,_ the data in this file is only stored in one logical place in IPFS (addressed by its hash).

The IPFS command-line tool can seamlessly follow the directory link names to traverse the file system:

chris@chris-VBox:~/tmp$ ipfs cat Qma3qbWDGJc6he3syLUTaRkJD3vAq1k5569tNMbUtjAZjf/my\_dir/my\_file.txt  
Hello World!

**Versioned File Systems**

IPFS can represent the data structures used by Git to allow for versioned file systems. The Git commit objects are described in the [Git Book](http://www.git-scm.com/book/en/v2/Git-Internals-Git-Objects#Commit-Objects). The structure of IPFS Commit object is not fully specified at the time of this writing, the [discussion is ongoing](https://github.com/ipfs/notes/issues/23).

The main properties of the Commit object is that it has one or more links with names _parent0_, _parent1_ etc pointing to previous commits, and one link with name _object_ (this is called _tree_ in Git) that points to the file system structure referenced by that commit.

We give as an example our previous file system directory structure, along with two commits: The first commit is the original structure, and in the second commit we’ve updated the file _my_file.txt_ to say _Another World!_ instead of the original _Hello World!._

![](https://cdn-images-1.medium.com/freeze/max/60/1*84YPXEWxIyuH7WGousjsjg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*84YPXEWxIyuH7WGousjsjg.jpeg)

Note also here that we have automatic deduplication, so that the new objects in the second commit is just the main directory, the new directory _my_dir,_ and the updated file _my_file.txt._

**Blockchains**

This is one of the most exciting use cases for IPFS. A blockchain has a natural DAG structure in that past blocks are always linked by their hash from later ones. More advanced blockchains like the [Ethereum](https://ethereum.org/) blockchain also has an associated state database which has a [Merkle-Patricia tree](https://github.com/ethereum/wiki/wiki/Patricia-Tree) structure that also can be emulated using IPFS objects.

We assume a simplistic model of a blockchain where each block contains the following data:

*   A list of transaction objects
*   A link to the previous block
*   The hash of a state tree/database

This blockchain can then be modeled in IPFS as follows:

![](https://cdn-images-1.medium.com/freeze/max/60/1*Vk9w5CXlRdp4T10UTpEYXg.jpeg?q=20)

![](https://cdn-images-1.medium.com/max/2000/1*Vk9w5CXlRdp4T10UTpEYXg.jpeg)

We see the deduplication we gain when putting the state database on IPFS — between two blocks only the state entries that have been changed need to be explicitly stored.

An interesting point here is the distinction between storing data on the blockchain and storing hashes of data on the blockchain. On the Ethereum platform you pay a rather large fee for storing data in the associated state database, in order to minimize bloat of the state database (“blockchain bloat”). Thus it’s a common design pattern for larger pieces of data to store not the data itself but an IPFS hash of the data in the state database.

If the blockchain with its associated state database is already represented in IPFS then the distinction between storing a hash on the blockchain and storing the data on the blockchain becomes somewhat blurred, since everything is stored in IPFS anyway. and the hash of the block only needs the hash of the state database.

In this case if someone has stored an IPFS link in the blockchain we can seamlessly follow this link to access the data as if the data was stored in the blockchain itself.

We can still make a distinction between on-chain and off-chain data storage however. We do this by looking at what miners need to process when creating a new block. In the current Ethereum network the miners need to process transactions that will update the state database. To do this they need access to the full state database in order to be able to update it wherever it is changed.

Thus in the blockchain state database represented in IPFS we would still need to tag data as being “on-chain” or “off-chain”. The “on-chain” data would be necessary for miners to retain locally in order to mine, and this data would be directly affected by transactions. The “off-chain” data would have to be updated by users and would not need to be touched by miners.

by [Dr. Christian Lundkvist](https://twitter.com/ChrisLundkvist), Director of Engineering, and [John Lilic](https://twitter.com/johnlilic), ConsenSys Enterprise