compression techniques GZip vs ZSTD ... what are the other compression techniques
zstd with dictionary - what are the other compression techniques , pros /cons
UTF8  encoding vs other encoding
how are documents stored in nosql database like cosmos 
what does the payload of the document mean and how can they be tweaked across different no sql databases 

how can compression cost or add to cpu cost ?
CPU Bound vs IO Bound ?
index policy ? What is the impact of index policy on performance /cost and latency ?
point query vs point read  , how does this play with cost and performance ? What are the other querying patterns for nosql dbs 

querying against index vs querying against document store ? What is the cost and performance advantage ? What happens if everything gets served by index ?

patch vs put what saves money / saves latency


How Amazon Dynamo works ?

- They do consistent hashing to partition data and scalability

- They use virtual nodes to prevent the hot shard problem  // TODO virtual nodes

- They replicate data across many servers for durability

- They use sloppy quorum for data consistency  // TODO Sloppy quorum 

- They use vector clocks to find the latest data version // To do vector clocks 

- They let the client logic resolve data conflicts

- They use hinted handoff to handle temporary failures //TODO hinted hand off

- They use Merkle trees to synchronize servers and handle permanent failures //TODO Merkle Trees

- They use gossip protocol for service discovery and failure detection //TODO Gossip protocol
