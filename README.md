# IPFS


***Raw Notes***

## Synopsis

IPFS stands for InterPlanetary File System, and it is a way of storing and sharing data in a decentralized network. It uses a data structure called a Merkle DAG (Directed Acyclic Graph) and a distributed network layer to store files. When a file is added to the network, it is given a unique "hash" that identifies it, and it is broken down into chunks and distributed among the nodes. This makes the network resilient to attacks and outages, so that files can still be accessed even if some of the nodes are compromised.

## Details


This markdown blog is a reference and summary of how IPFS works, broken down into logical concepts and components.

IPFS is a distributed, peer-to-peer protocol designed to store and share data in a decentralized network. This eliminates the need for a centralized server, which is vulnerable to attacks and outages. Instead, data is stored in a distributed manner on nodes all over the world, and is accessible by its cryptographic hash.

At the core of IPFS is a data structure known as a Merkle DAG (Directed Acyclic Graph). This structure enables IPFS to store all kinds of data, and makes IPFS versatile in its uses. It also enables IPFS to detect any changes in data, as any modification will create a new cryptographic hash, so that all nodes have up-to-date versions of a file. This enables content addressing, which allows users to simply provide the cryptographic hash to access the file, instead of needing to know the exact location.

Another key component of IPFS is its distributed network layer. This is made up of the network of nodes, which all store some or all of the data from the Merkle DAG. The data is distributed and stored in a highly-reliable manner, ensuring that it is always available.

Finally, IPFS also includes some protocol logic, which is responsible for routing messages, as well as creating and verifying content addresses.

To understand how IPFS works its important to understand the individual stages that a file would go through in IPFS.

These stages can be broken down into Importing, Naming, Finding, and Fetching. The Import step happens when we first add content to the network, Name is used to create a permanent link to content, Find is used to locate content, and Fetch is used to retrieve content.IPFS works by assigning each file a unique "hash" that identifies it. This hash is then stored on the network, allowing each node to locate and retrieve the file. Files are broken down into chunks and distributed among the nodes, so that they can be retrieved even if some of the nodes are offline. In addition, the system is designed to be resilient to attacks and failures, allowing users to access files even if some of the nodes are compromised.

![IPFS](https://user-images.githubusercontent.com/38284764/206791995-5f9f3729-b414-4002-ad2b-1e4c85ea4118.png)

# Import
***You have files, IPFS wants you to add those files, this is how we do it***

- Chunk the file into pieces
- take the pieces and compile them into files and directories
- Then code them in the IPLD data structure

### Chunking

The first thing we do in order to import a file with IPFS is we use chunking to take a file and break it down into tiny pieces. This allows for faster storage and retrieval of data and better security and reliability as well as the ability to `seek` through a file since the file is chunked into smaller pieces. 

### UnixFS

Now that we have chunked the file we still need to have a way to create a contiguous file out of the pieces. So we get to utilize a Data Structure similar to a Merkle Tree called a Merkle DAG. A Merkle Tree is a data structure used in cryptography and computer science to verify the integrity of data. It is composed of digital hashes that link data blocks together in a secure way. By comparing a root hash with the hash of the data set, users can verify the integrity of the data without needing to check the whole data set. UnixFS is a data structure created by IPFS that lets people store and access unstructured data in a distributed and decentralized way. It is designed to store data of any type and format, and also stores associated metadata. UnixFS's structure is slightly different than Merkle Tree because trees can't have two edges point to the same thing but a graph of course can. 

### Merkle DAG

A Merkle DAG (Directed Acyclic Graph) is a type of data structure used in distributed computing to enable efficient and secure information sharing. The Merkle DAG is used in distributed systems to coordinate peer-to-peer (P2P) transactions while ensuring data integrity and authenticity. The main feature of the Merkle DAG is its ability to create an efficient and secure way to store transactions. Using a Merkle DAG, transactions can be grouped together in a way that makes them difficult to tamper with or reverse. The graph structure allows for the node-to-node transmission of data, and can be used for various applications such as timestamping and distributed ledger protocols.

### IPLD

IPLD (InterPlanetary Linked Data) is a data model and set of protocols for linking and sharing data across distributed systems. It is based on the Merkle DAG data structure and is used to create a unified data structure for distributed systems. IPLD is used in conjunction with IPFS to enable data to be linked and shared across multiple systems, allowing for more efficient data storage and retrieval.

# Name

***Decentralized web technology lets users access data without relying on central authorities. Content addressing, which uses cryptographic hashing to give data a unique and secure identifier, makes it easy to trust data shared on the decentralized web and to rely on peers for content. Hashes act as links, not just names, freeing users from reliance on domain location. This is essential for creating a secure, trustworthy web.***

- use a content id (cid) to refer to the pieces of data
- use paths to describe extra meta data about the cid or data we are addressing
- Use ipns for creating mutable names

### CID
CID (Content Identifier) is a unique identifier used in IPFS to identify content. It is a hash of the content's data and is used to locate and retrieve the content from the distributed network. CID is used to ensure the integrity of the content and to ensure that the content is not tampered with.

### Path

A Path in IPFS is a string of characters that is used to locate and retrieve content from the distributed network. It is composed of the CID of the content and the path of the content within the Merkle DAG. Paths are used to locate and retrieve content from IPFS, allowing for more efficient storage and retrieval of data.

### IPNS

IPNS (InterPlanetary Name System) is a distributed naming system used in IPFS to locate and retrieve content from the distributed network. It is based on the Merkle DAG data structure and is used to create a unified data structure for distributed systems. IPNS is used to create a permanent link to content, allowing for more efficient storage and retrieval of data.


# Find
***You want something on IPFS? We have to find it. But remember we don't access things by location like the centralized web. 
On the decentralized web, content can be requested using its content address (hash). This address acts like a link, and allows us to get the exact file we need from any peer who has it, even if the original publisher is not online.*** 

- Use content routing via the Kademlia DHT

### Routing 
Routing in IPFS is the process of finding and retrieving content from the distributed network. It is based on the Kademlia distributed hash table (DHT) and is used to locate and retrieve content from the distributed network. Routing is used to ensure that content is stored and retrieved efficiently, allowing for more efficient storage and retrieval of data.

### DHT
DHT (Distributed Hash Table) is a data structure used in distributed systems to store and retrieve data. It is used in IPFS to store and retrieve content from the distributed network. DHT is used to ensure that content is stored and retrieved efficiently, allowing for more efficient storage and retrieval of data.

### Kademlia
Kademlia is a distributed hash table (DHT) used in IPFS to store and retrieve content from the distributed network. It is based on the XOR metric and is used to ensure that content is stored and retrieved efficiently. Kademlia is used to ensure that content is stored and retrieved efficiently, allowing for more efficient storage and retrieval of data.


# Fetch

***Now that we found it wee need to Fetch it. For that we use Bitswap which is a message-based protocol that can be used to quickly exchange data between peers.***

 - Use Bitswap

### Bitswap
Bitswap is a protocol used in IPFS to exchange data between peers. It is designed to be simple and efficient, with the ability to balance aspects such as throughput, latency, fairness, and memory usage. When a wantlist is received, the server responds with either information about the block or the block itself. When blocks are received, a Cancel notification is sent to peers that have requested the data.


