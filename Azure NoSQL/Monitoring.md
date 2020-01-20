Monitoring

Azure Cosmos DB provides metrics for throughput, storage, consistency, availability, and latency. The Azure portal provides an aggregated view of these metrics. You can also view Azure Cosmos DB metrics from Azure Monitor API.

#### Determine how many requests are succeeding or causing errors
The most common error status code is 429 (rate limiting/throttling). This error means that requests to Azure Cosmos DB are more than the provisioned throughput. The most common solution to this problem is to scale up the RUs for the given collection.

## Troubleshooting throttled requests or poor performance

#### Determine the throughput distribution across partitions
Having a good cardinality of your partition keys is essential for any scalable application. To determine the throughput distribution of any partitioned container broken down by partitions, go to the Metrics page in the portal. In the Throughput tab, the storage breakdown is shown in the Max consumed RU/second by each physical partition chart. A skewed graph indicates a hot partition, which can result in throttled requests and may require repartitioning. 

#### Determine the storage distribution across partitions
Having a good cardinality of your partition is essential for any scalable application. To determine the storage distribution of any partitioned container broken down by partitions, head to the Metrics blade in the Azure portal. In the Storage tab, the storage breakdown is shown in the Data + Index storage consumed by top partition keys chart. After identifying which partition key is causing the skew in distribution, you may have to repartition your container with a more distributed partition key.

#### Determine data size against index size
In Azure Cosmos DB, the total consumed storage is the combination of both the Data size and Index size. Typically, the index size is a fraction of the data size. In the Metrics blade in the Azure portal, the Storage tab showcases the breakdown of storage consumption based on data and index.

#### Determine why queries are running slow
QueryMetrics provides details on how long each component of the query took to execution. The most common root cause for long running queries is scans, meaning the query was unable to leverage the indexes. This problem can be resolved with a better filter condition.

***
#### Set an alert
The three steps of setting an alert for a resource:
1. The name of the alert rule you are setting up.
2. The condition, threshold, and period that determine when the alert activates. For example, a server error count greater than 5 over the last 15 minutes.
3. Who are emailed when the alert fires.

***
## Logging 
What is logged by Azure Diagnostic Logs?
- All authenticated backend requests (TCP/REST) across all APIs are logged, including failed requests as a result of access permissions, system errors, or bad requests. Support for user-initiated Graph, Cassandra, and Table API requests aren't currently available.
- Operations on the database itself, which include CRUD operations on all documents, containers, and databases.
- Operations on account keys, which include creating, modifying, or deleting the keys.
- Unauthenticated requests that result in a 401 response. For example, requests that don't have a bearer token, or are malformed or expired, or have an invalid token.
