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

- Reference: https://newsletter.systemdesign.one/p/amazon-dynamo-architecture

- They do consistent hashing to partition data and scalability

- They use virtual nodes to prevent the hot shard problem  // TODO virtual nodes

- They replicate data across many servers for durability

- They use sloppy quorum for data consistency  // TODO Sloppy quorum 

- They use vector clocks to find the latest data version // To do vector clocks 

- They let the client logic resolve data conflicts

- They use hinted handoff to handle temporary failures //TODO hinted hand off

- They use Merkle trees to synchronize servers and handle permanent failures //TODO Merkle Trees

- They use gossip protocol for service discovery and failure detection //TODO Gossip protocol


Database scaling
![image](https://github.com/learningdebunked/Database/assets/7702406/26efc15d-5d57-45c9-9679-bedcfe6cb926)


Relational data model -- Developed by EF Codd

Main components of relational data model of EF Codd
      Relations
      Domains 
      tuples



      ****Covering Indexes****

      Don’t index just filters. Index what you need.

If you index only your WHERE columns, you leave performance on the table.

One of the most effective yet overlooked techniques is Covering Indexes. 

Unlike standard indexes that only help filter rows, covering indexes include all columns required for a query.

It will reduce query execution time by eliminating the need to access the main table.

𝗪𝗵𝘆 𝗖𝗼𝘃𝗲𝗿𝗶𝗻𝗴 𝗜𝗻𝗱𝗲𝘅𝗲𝘀?

• By including all required columns, the query can be resolved entirely from the index, avoiding table lookups.
• Can speed up join queries by reducing access to the base table.

𝗖𝗼𝗹𝘂𝗺𝗻𝘀 𝘁𝗼 𝗜𝗻𝗰𝗹𝘂𝗱𝗲:

• WHERE: Filters rows.
• SELECT: Data to retrieve.
• ORDER BY: Sorting columns.

𝗦𝘁𝗲𝗽𝘀 𝘁𝗼 𝗖𝗿𝗲𝗮𝘁𝗲 𝗖𝗼𝘃𝗲𝗿𝗶𝗻𝗴 𝗜𝗻𝗱𝗲𝘅𝗲𝘀

1- Use execution plans to identify queries that perform frequent table lookups.
2- Focus on columns in WHERE, SELECT, and ORDER BY.
3- Don’t create multiple indexes with overlapping columns unnecessarily.

𝗖𝗼𝘃𝗲𝗿𝗶𝗻𝗴 𝗜𝗻𝗱𝗲𝘅𝗲𝘀 𝗮𝗿𝗲 𝗻𝗼𝘁 𝗳𝗼𝗿 𝗳𝗿𝗲𝗲.

• Each insert, update, or delete operation must update the index, which can slow down write-heavy workloads.
• Covering indexes consumes more disk space.

Covering indexes are a powerful tool for database performance, especially for read-heavy applications. 
While they can increase write costs, the trade-off is often worth it for the dramatic speedups in query performance. 
Every table lookup wastes precious time. Fix it!
