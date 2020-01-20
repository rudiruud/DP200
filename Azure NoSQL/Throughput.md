Throughput

#### Throughput
*In Azure Cosmos DB, provisioned throughput is represented as request units/second (RU/s or the plural form RUs). RUs measure the cost of both read and write operations against your Cosmos container.*

Adequate throughput is important to ensure you can handle the volume of transactions for your business needs. In Azure Cosmos DB, you provision throughput for your containers to perform writes, reads, updates, and deletes. You can provision throughput for an entire database and have it shared among containers within the database. You can also provision throughput dedicated to specific containers.

To scale throughput strategically, you need to estimate your throughput needs by estimating the number of operations you'll have to support at different times. If your requests consume all of the provisioned throughput, Azure Cosmos DB will rate-limit your requests. Operations will have to wait and retry, likely causing higher latency.

Azure Cosmos DB measures throughput using something called a **request unit (RU)**. Request unit usage is measured per second, so the unit of measure is request units per second (RU/s). You must reserve the number of RU/s you want Azure Cosmos DB to provision in advance, so it can handle the load you've estimated, and you can scale your RU/s up or down at any time to meet current demand.

A single request unit, 1 RU, is equal to the approximate cost of performing a single GET request on a 1-KB document using a document's ID. Performing a GET by using a document's ID is an efficient means for retrieving a document, and thus the cost is small. Creating, replacing, or deleting the same item requires additional processing by the service, and therefore requires more request units.

**You can provision RUs on a Cosmos container or a Cosmos database. RUs provisioned on a container are exclusively available for the operations performed on that container. RUs provisioned on a database are shared among all the containers within that database (except for any containers with exclusively assigned RUs).**

https://docs.microsoft.com/en-us/azure/cosmos-db/scaling-throughput
***
#### Throughput between different zones 
If you provision 'R' RUs on a Cosmos container (or database), Cosmos DB ensures that 'R' RUs are available in each region associated with your Cosmos account. Each time you add a new region to your account, Cosmos DB automatically provisions 'R' RUs in the newly added region. The operations performed against your Cosmos container are guaranteed to get 'R' RUs in each region. You can't selectively assign RUs to a specific region. The RUs provisioned on a Cosmos container (or database) are provisioned in all the regions associated with your Cosmos account.

##### Throughput and Consistency model choice
Your choice of consistency model also affects the throughput. You can get approximately 2x read throughput for the more relaxed consistency levels (e.g., session, consistent prefix and eventual consistency) compared to stronger consistency levels (e.g., bounded staleness or strong consistency).