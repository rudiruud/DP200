Performance Tuning

***
#### Analyzing Throughput
Data is written to CosmosDB via HTTPs. When throughput reaches the limit, a HTTPS Code 429 code is returned (rate limit exceded). 

1. **Partition bottlenecks**
   - A single hot partition may become a bottleneck in the overal query retrieval process. In the throughput and storage tab in Azure portal, you can review how partitions are used compared to eachother.
2. **Resource bottlenecks**:
   - When quering documents in the data explorer, the query stats display the used throughput.
   - When using multi-master geo replication, stronger consistency will have an impact at performace (especially write).
3. **Query tuning**: 
   - Reading a document directly from your Azure Cosmos DB collection by using its id and partition key values is the least expensive operation. If you constrict your queries to this you might be able to do without indexing (which increases your write performance)
   - Quering across partitions will require more RUs  than querying inside a single partition. When querying on keys that are not indexed/ partitioned, a scan across partitions is required.
   - Quering with functions may hamper performance. Only a few functions (that read strings from left to right) include the usage of indexes in their scan. 

***
#### Indexing
n Azure Cosmos DB, every container has an indexing policy that dictates how the container's items should be indexed. The default indexing policy for newly created containers indexes every property of every item, enforcing range indexes for any string or number, and spatial indexes for any GeoJSON object of type Point. This allows you to get high query performance without having to think about indexing and index management upfront.

The three indexing modes you can use with Azure Cosmos DB are:

- **Consistent**: The index is updated synchronously every time a new document is written to the collection. New queries on the collection use the updated index right away. Query results are consistent with the updated documents in the collection.
- **None**: No index is created. Queries are expensive on collections that aren't indexed. If you're using your Azure Cosmos DB collection to read records directly rather than querying the collection, it's possible to avoid the overhead of indexing.
- Not recommended:
  - **Lazy Indexing**: The index is updated at a lower priority. The reads and writes from the collection take a higher priority. In lazy mode, writes are cheaper because the index isn't updated immediately. When the index is fully updated depends on the demands on the collection. Query results don't include the updated documents until the index is consistent with the collection.

You can change the index configuration at any time. A custom indexing policy can specify property paths that are explicitly included or excluded from indexing. By optimizing the number of paths that are indexed, you can lower the amount of storage used by your container and improve the latency of write operations. 


***
