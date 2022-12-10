# How IPFS Works?
### A logical breakdown of the components and concepts of IPFS

## What is IPFS?

IPFS stands for InterPlanetary File System, and it provides us a way of storing and sharing data in a decentralized manner. When a file is added to the IPFS network, it is given a unique "hash" that identifies it, and it is broken down into chunks and distributed among the nodes. You don't access files in IPFS by the location like you do in the centralized web, `i.e superman.com/upupandaway.jpg`,
instead you notify IPFS which piece of content you desire to retrieve by using its unique hash, then IPFS uses that hash to locate the content somewhere on the network and provide it to you. 

## Why IPFS?

IPFS is a distributed, peer-to-peer protocol designed to store and share data in a decentralized network. This eliminates the need for a centralized server, which is vulnerable to attacks and outages. Instead, data is stored in a distributed manner on nodes all over the world, and is accessible by its cryptographic hash.

At the core of IPFS is a data structure known as a Merkle DAG (Directed Acyclic Graph). This structure enables IPFS to store all kinds of data, and makes IPFS versatile in its uses. It also enables IPFS to detect any changes in data, as any modification will create a new cryptographic hash, so that all nodes have up-to-date versions of a file. This enables content addressing, which allows users to simply provide the cryptographic hash to access the file, instead of needing to know the exact location.

Another key component of IPFS is its distributed network layer. This is made up of the network of nodes, which all store some or all of the data from the Merkle DAG. The data is distributed and stored in a highly-reliable manner, ensuring that it is always available.

IPFS can be used for a variety of purposes, including hosting websites, sharing files, and building decentralized applications. Some of the main benefits of using IPFS include:

1. Improved security: IPFS uses cryptographic hashes to ensure the integrity and security of data stored on the network. This means that data cannot be tampered with or altered once it has been added to the network.

1. Decentralization: IPFS is a decentralized network, meaning that it is not controlled by any single entity. This makes it more resistant to censorship and other forms of control.

1. Faster loading times: Because IPFS is a distributed system, data is stored on multiple nodes across the network. This means that users can access the data more quickly, since it is likely to be stored on a node that is geographically closer to them.

1. Improved scalability: As the IPFS network grows, it becomes more scalable and able to handle a larger amount of data and traffic. This means that it can support more users and applications without experiencing performance issues.

Overall, IPFS provides a number of benefits that make it a useful tool for storing and sharing data in a decentralized and secure manner.


# Understanding IPFS

![IPFS](https://user-images.githubusercontent.com/38284764/206810067-61c626a2-dded-4ee4-bb19-f4b595a000d6.png)

To understand how IPFS works its important to understand the individual stages that a file would go through in IPFS.

These stages can be broken down into ***Importing, Naming, Finding, and Fetching***. The _Import_ step happens when we first add content to the network, _Naming_ happens when we create a means to link to the content but not with a file location, but instead using ***content based addressing***, _Finding_ is when we locate content contained in IPFS, and _Fetch_ is used to retrieve content that we have found. 

# Import
***You have files, IPFS wants you to add those files, this is how we do it***

Steps:
- Chunk the file into pieces
- Take the pieces and compile them into files and directories
- Then code them in the IPLD data structure

### Chunking

The first thing we do in order to import a file with IPFS is chunking. We use chunking to take a file and break it down into smaller pieces. This allows for faster storage and retrieval of data.

### UnixFS

Now that we have chunked the file we still need to have a way to create a contiguous file out of the pieces. So we get to utilize a Data Structure similar to a Merkle Tree called a Merkle DAG. A Merkle Tree is a data structure used in cryptography and computer science to verify the integrity of data. It is composed of digital hashes that link data blocks together in a secure way. By comparing a root hash with the hash of the data set, users can verify the integrity of the data without needing to check the whole data set. 

UnixFS is a data structure created by IPFS that lets people store and access unstructured data in a distributed and decentralized way. It is designed to store data of any type and format, and also stores associated metadata. UnixFS's structure is slightly different than Merkle Tree because trees can't have two edges point to the same thing. If you are not fammiliar with Graphs, endges are essentially the lines or connections and nodes are the things being connected.

![MerkleDag](https://user-images.githubusercontent.com/38284764/206813371-207be774-9512-4027-9ba0-8a99a767f78a.png)

In the above example you can see `Main Directory` is a Node and there is an edge that connects to `Project directory`. In this example also you can see the `Project directory` and `Todo directory` both point to the `Todo.js` file. 

In this example this would be because both directories contain identical files. IPFS is efficient enough to know that two files are identical and as a result this example just has both directories reference the same file. In location based systems you would just end up with two redundant identical files.

### Merkle DAG

A Merkle DAG (Directed Acyclic Graph) is a type of data structure used in distributed computing to enable efficient and secure information sharing. The Merkle DAG is used in distributed systems to coordinate peer-to-peer (P2P) transactions while ensuring data integrity and authenticity. The main feature of the Merkle DAG is its ability to create an efficient and secure way to store transactions. Using a Merkle DAG, transactions can be grouped together in a way that makes them difficult to tamper with or reverse. The graph structure allows for the node-to-node transmission of data, and can be used for various applications such as timestamping and distributed ledger protocols.

### IPLD

IPLD (InterPlanetary Linked Data) is a data model and set of protocols for linking and sharing data across distributed systems. It is based on the Merkle DAG data structure and is used to create a unified data structure for distributed systems. IPLD is used in conjunction with IPFS to enable data to be linked and shared across multiple systems, allowing for more efficient data storage and retrieval.

# Name

***Decentralized web technology lets users access data without relying on central authorities. Content addressing, which uses cryptographic hashing to give data a unique and secure identifier, makes it easy to trust data shared on the decentralized web and to rely on peers for content. Hashes act as links, not just names, freeing users from reliance on domain location. This is essential for creating a secure, trustworthy web.***

Steps:
- Use a content id (cid) to refer to the pieces of data
- Use paths to describe extra metadata about the cid or data we are addressing
- Use IPNS for creating mutable names

### CID
CID (Content Identifier) is a unique identifier used in IPFS to identify content. It is a hash of the content's data and is used to locate and retrieve the content from the distributed network. CID is used to ensure the integrity of the content and to ensure that the content is not tampered with.

### Path

A Path in IPFS is a string of characters that is used to locate and retrieve content from the distributed network. It is composed of the CID of the content and the path of the content within the Merkle DAG. Paths are used to locate and retrieve content from IPFS, allowing for more efficient storage and retrieval of data.

### IPNS

IPNS (InterPlanetary Name System) is a distributed naming system used in IPFS to locate and retrieve content from the distributed network. IPNS is used to create a permanent link to content, allowing for more efficient storage and retrieval of data.


# Find
***You want something on IPFS? We have to find it. But remember we don't access things by location like the centralized web. 
On the decentralized web, content can be requested using its content address (hash). This address acts like a link, and allows us to get the exact file we need from any peer who has it, even if the original publisher is not online.*** 

Steps:
- Use content routing via the Kademlia DHT

### Routing 
Routing in IPFS is the process of finding content on the distributed network. We know what content we want but we don't yet know who has the content. We need to figure who has the content, so then it can eventually be retrieved by us. Routing is used to ensure that content is stored and retrieved efficiently.

### DHT
DHT (Distributed Hash Table) is a data structure used in distributed systems to store and retrieve data. It is used in IPFS to store and retrieve content from the distributed network. The DHT is what actually would know which peers have what content. IPFS uses a distributed hash table (DHT) as a content routing system to help users find the data they are looking for. The DHT acts as a directory where peers store and find data, allowing users to quickly map what they are looking for to the peer that is storing the content.

### Kademlia
The Kademlia algorithm has been around for a while, and is used to build a distributed hash table on top of three system parameters: 
1. An address space as a way that all of the network peers can be uniquely identified
1. A metric to order peers in the address space
1. A projection to calculate where the data should be stored. 
 
Having this address space and a peer ordering metric allows us to search the network as though it was a sorted list i.e [1,2,3,4,5].


# Fetch

***Now that we found it we need to Fetch it. For that we use Bitswap which is a message-based protocol that can be used to quickly exchange data between peers.***

Steps:
 - Use Bitswap to retrieve data

### Bitswap
Bitswap is a protocol used in IPFS to exchange data between peers. It is designed to be simple and efficient, with the ability to balance aspects such as throughput, latency, fairness, and memory usage. When a wantlist is received, the server responds with either information about the block or the block itself. When blocks are received, a Cancel notification is sent to peers that have requested the data.


# Conclusion
There's so much to learn about the features and components of IPFS, we hope this has been an informative introduction, and we hope your journey is only just getting started. 

## Review Questions

**❓ In your own words what happens when you add a file to IPFS? (Import)**

**❓ How would you describe content based addressing and how is it different from the way things work in the centralized web?**

**❓ In your own words what is the purpose of a Distributed Hash Table (DHT) in IPFS?**



