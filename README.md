# Redis

Redis is used as a

- Database
- Cache
- Message broker

Can be visualized Redis as:  MongoDB + MemCached

## Features

- Flexible, mostly because of NoSQL db
- Very fast: 110,000 sets/seconds and 81,000 gets/seconds
- Rich datatype support, *refer datatype section below*
- replication, master-slave, Asynchronous replication, runs on HA(really huge topic by itself)
- Support multiple data structure
- Caching and Disk persistance
  - by default data is saved in memory
  - there are two type of persistance mode available: **RDB** and **AOF**(Append only file) *read the difference*
  - **RDB**: use **dbfilename dump.rdb**
    - on high level, RDB is faster as Redis will take a snapshot and dump it on a file. The we can mount to persist that data.
  - **AOF**: use **appendonly yes** and **appendfilename "filename.aof"**
    - on the other hand, writes each operation on the file, it guarantees higher durability and minimal loss.
  - Redis can run on both mode and that is safest
- Secured:
  - its always used by trusted clients
  - never used to internet or external use *its always used by a application, and not directly*
  - data encryption not supported
  - simple authentication can be setup **requirepass password** is the configuration key that is used to set password.
  - can be restricted to certain interfaces  
  - TLS support from version 6, disable by default

## As a Database

As a database we can visualize Redis as a NoSQL Key-Value store database.

## Redis Datatypes

- String
- Lists: always list of strings
- Sets:
- Sorted Sets:
- Hashes: key value pair, very similar to javascript objects
- Bitmaps
- Hyperlogs
- Geospatial Indexes

## How programming language interact with Redis, and which are supported

- Programming language uses clients, Redis have language specific clients.

Almost all programming language are supported.
