Partitioning

***
#### Partition Keys
If you continue to add new data to a single server or a single partition, it will eventually run out of space. To prepare for this, you need a partitioning strategy to scale out instead of up. Scaling out is also called horizontal scaling, and it enables you to add more partitions to your database as your application needs them. 

*Once the partition key is set, it cannot be changed (or a new one added) without recreating the container, so selecting the right partition key is an important decision to make early in your development process.*

##### Avoiding hot partitions
A partition key should aim to distribute operations across the database. You want to distribute requests to avoid hot partitions. A hot partition is a single partition that receives many more requests than the others, which can create a throughput bottleneck. CosmosDB cannot allocate throughputs to specific partitions.

Best practices include:
- Don’t be afraid of choosing a partition key that has a large number of values. The more values your partition key has, the more scalability you have.
- To determine the best partition key for a read-heavy workload, review the top three to five queries you plan on using. The value most frequently included in the WHERE clause is a good candidate for the partition key.
- For write-heavy workloads, you'll need to understand the transactional needs of your workload, because the partition key is the scope of multi-document transactions.

***
#### Partition Strategy

An effective partitioning strategy distributes data and access evenly across partitions, and across time. Querying documents from within the same partition is less expensive than querying across partitions.

You choose how to partition your data at design time. The partitioning configuration can't be changed after a collection is provisioned. Date is often an unwise choice btw. 