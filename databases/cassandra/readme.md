## Cassandra
- Cassandra is a distributed database based on nodes - leaderless - ring network - p2p.    
- Nodes can be scaled horizontally(preferred) (add or remove nodes) and also vertically (add more resources on the same 
node without downtime.  



## Why? 


## Distributed NOSQL 

## Terminology
### Node
- 1 installation = 1 node
- capacity = 2 ~4 TB (ssd or rotational disks)
- Througput = 6k-12k tx/sec/core
- Runtime = JVM
- Language = Java
- Node can run anywhere(onprem, cloud..)

Node contains data, which is hashed based on partition key.  

Node mangement is done through `nodetool`  

#### Co-ordinator node
There is no concept of leader and follower. All nodes are leaders or in cassandra terms Co-ordinator Nodes.
Client/Driver can talk to any node that is closer and that node becomes the Co-ordinator node.  
The co-ordinator node checks the data and partition hash, finds the node which is storing data and send it to the node.  
The node recieves, writes and acknowledges the co-ordinator which responds the client.

> Note: The Ring Nodes are structured by order(sort) based on hash. so any co-ordinator node can easily find the respective
> node quickly (similar to binary search). Hashes on each node are ordered.

#### Partitoner (md5, murmur)
Partitioner is process that runs in cassadra which makes sure that nodes are evenly loaded. (not overloaded or under utilised)

### Gossip protocol

### Datacenter
Geographic distribution
Multi cloud & Hybrid cloud

Perfromance

### Keyspace
### Partition key
### Clustering key
### Data columns
### Replication factor


## Main Concepts

### Partition & Clustering keys

Node - Partitionkey - Partition Tokens

Keyspace -> Table

Table -> PartionKey + Clustering keys + Data columns

Rules of partitions

### Data modelling - Denomarmalisation

Application flow

###  CRUD - Nodejs client


### Replication
Replication factor

## CAP Theorem
- High Availability

How Consistency is established? 
Immediate Consistency

