Replication

**Key distinction: Replication/ Distribution does not always mean replication of writes.**

#### Global Distribution
Global distribution enables you to replicate data from one region into multiple Azure regions. You can add or remove regions in which your database is replicated at any time, and Azure Cosmos DB ensures that when you add an additional region, your data is available for operations within 30 minutes, assuming your data is 100 TBs or less. Replicating the database globally can lower the latency due to network. 

***
#### Fail-overs
Once you've replicated your data in multiple regions, you can take advantage of the automated failover solutions Azure Cosmos DB provides. **Automated failover **is a feature that comes into play when there's a disaster or other event that takes one of your read or write regions offline, and it redirects requests from the offline region to the next most prioritized region. When Azure detects read or write errors, it automatically disconnects CosmosDB and another CosmosDB takes over.

Once you add a second region, the Manual Failover option is enabled on the Replicate data globally page in the portal. You can use this option to test the failover process or change the primary write region. Once you add a third region, the Failover Priorities option is enabled on the same page so that you can change the failover order for reads.

https://docs.microsoft.com/en-us/azure/cosmos-db/tutorial-global-distribution-sql-api
***
#### Multi-master Support (Multi-Write)
Multi-master support is an option that can be enabled on new Azure Cosmos DB accounts. Once the account is replicated in multiple regions, each region is a master region that equally participates in a write-anywhere model, also known as an active-active pattern.

Azure Cosmos DB regions operating as master regions in a multi-master configuration automatically work to converge data written to all replicas and ensure global consistency and data integrity. With Azure Cosmos DB multi-master support, you can perform writes on any container in a write-enabled region world-wide. Written data is propagated to all other regions immediately.

***
#### Consistency levels between zones
With the introduction of multi-master geo replication comes the issue of how consistent data between databases should be. 

Assume that a record is inserted into database 1 (without any conflicts), how certain do you to be that this record is also returned in database 2 when queried just a fraction layer. Normally in distributed databases, there are two flavours to choose from:
- Strong consistency (ensure that the DB is up to date before returning a result)
- Eventual consistency (return a result first and check if DB is up to date later)

With CosmosDB, there are five consistency choices:
At one end of the spectrum is Strong consistency, which offers a linearizability guarantee with the reads guaranteed to return the most recent version of an item. At the other end of the spectrum is Eventual consistency, which guarantees that in absence of any further writes, the replicas within the group eventually converge. In the middle is Session consistency, which is the most popular because it guarantees monotonic reads, monotonic writes, and read your own writes (RYW) guarantees.

The main consistency levels are:
- **Strong**: Linearizability. Reads are guaranteed to return the most recent version of an item. A write is either synchronously committed durably by both the primary and the quorum of secondaries, or it is aborted.
- **Bounded Staleness**: Consistent Prefix. Reads lag behind writes by at most k prefixes or t interval.
- **Session**: Unlike the global consistency models offered by strong and bound
- **Consistent Prefix**: Updates returned are some prefix of all the updates, with no gaps. Consistent prefix guarantees that in absence of any further writes, the replicas within the group eventually converge.
- **Eventual**: Eventual consistency guarantees that in absence of any further writes, the replicas within the group eventually converge.

##### Effects of consistency on throughput
Your choice of consistency model also affects the throughput. You can get approximately 2x read throughput for the more relaxed consistency levels (e.g., session, consistent prefix and eventual consistency) compared to stronger consistency levels (e.g., bounded staleness or strong consistency).

##### Conflict resolution
With the addition of multi-master support comes the possibility of encountering conflicts for writes to different regions. Conflicts are rare in Azure Cosmos DB and can only occur w*hen an item is simultaneously changed in multiple regions, before propagation between the regions has happened*. Given the speed with which replication happens globally, you should not experience conflicts often, if at all. However, Azure Cosmos DB does provide conflict resolution modes that allow users to decide how to handle scenarios where the same record is updated simultaneously by different writers in two or more regions. There are three conflict resolution modes offered by Azure Cosmos DB.

- **Last-Writer-Wins (LWW)**, in which conflicts are resolved based on the value of a user-defined integer property in the document.
- **Custom** - User-defined function, in which you can fully control conflict resolution by registering a User-defined function to the collection. 
- **Custom - Async**, in which Azure Cosmos DB excludes all conflicts from being committed and registers them in the read-only conflicts feed for deferred resolution by the user’s application.


https://docs.microsoft.com/en-us/azure/cosmos-db/consistency-levels
