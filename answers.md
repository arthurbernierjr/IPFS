## Where is data stored on IPFS?
    - How is it accessed?
    - A: ***Data is stored on the individual peers that are part of the network, data is accessed using content addressing as opposed to the location of the data and has a CID.***
    
## What happens when content is ‘added’ to IPFS?
    - Where is the data, and what roles do peers and data structures play?
    - A: ***When content is added to IPFS, it is assigned a unique cryptographic hash that acts as a fingerprint for the data. This hash is used to identify and locate the data on the network, and it ensures the integrity and security of the data. Once the data has been hashed, it is divided into smaller chunks called blocks. These blocks are then distributed across the network, where they are stored on the nodes of participating users. The data is then available to be accessed by other users on the network. Users can retrieve the data by requesting the specific hash that corresponds to the content they want to access. The network will then use this hash to locate and retrieve the data from the nodes where it is stored. The DHT data structure is what stores what peers have what data. The Merkle DAG is the dtat structure that allows for directories to point to data that belongs in it and for chunks of files to point to pieces other chunks the same file treatings the the chunks as nodes of the graph.

## What are some of the technical ways (such as Content Addressing) that Web3 is different from Web2, and where do you predict people will have trouble and misconceptions?
