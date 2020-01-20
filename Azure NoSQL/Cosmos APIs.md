Cosmos APIs

Azure Cosmos DB was built to support multiple different models, and you can continue to use industry standard APIs if they are already part of your application or database design. It features four APIs:
- **Core API**: Core (SQL) is the default API for Azure Cosmos DB, which provides you with a view of your data that resembles a traditional NoSQL document store. You can query the hierarchical JSON documents with a SQL-like language. 
- **MongoDB API**: This API allows existing MongoDB client SDKs, drivers, and tools to interact with the data transparently, as if they are running against an actual MongoDB database. The data is stored in document format, which is the same as using Core (SQL).
- **Cassandra API**: Azure Cosmos DB's support for the Cassandra API makes it possible to query data by using the Cassandra Query Language (CQL), and your data will appear to be a partitioned row store. Just like the MongoDB API, any clients or tools should be able to connect transparently to Azure Cosmos DB; only your connection settings should need to be updated.
- **Azure Table API**: Azure Cosmos DB's Azure Table API provides support for applications that are written for Azure Table Storage that need premium capabilities like global distribution, high availability, scalable throughput. The original Table API only allows for indexing on the Partition and Row keys; there are no secondary indexes. Storing table data in Comsos DB automatically indexes all the properties, and requires no index management.
- **Gremlin (graph) API**: Choosing Gremlin as the API provides a graph-based view over the data. Remember that at the lowest level, all data in any Azure Cosmos DB is stored in an ARS format. A graph-based view on the database means data is either a vertex (which is an individual item in the database), or an edge (which is a relationship between items in the database).

![7f16330dd79ef381688873095b519230.png](../_resources/03e75a4a14b5440885ee26d727fd8eea.png)



***
#### API Naming Conventions

CosmosDB Entitiy | SQL | MongoDB | Cassandra (CQL) | Table | Gremlin
--- | --- | ---| --- | --- | ---
Container | Collection | Collection | Table | Table | Graph
Item | Document | Document | Row | Item | Node/Edge


***
#### Stored Procedures
Stored procedures perform complex transactions on documents and properties. Stored procedures are written in *JavaScript* and are stored in a container on Azure Cosmos DB. By performing the stored procedures on the database engine and close to the data, you can improve performance over client-side programming.

Stored procedures are the only way to achieve atomic transactions within Azure Cosmos DB; the client-side SDKs do not support transactions.

Performing batch operations in stored procedures is also recommended because of the reduced need to create separate transactions.

***
#### User Defined Functions (UDF)
UDFs are used to extend the Azure Cosmos DB SQL query language grammar and implement custom business logic, such as calculations on properties and documents. *UDFs can be called only from inside queries and, unlike stored procedures, they do not have access to the context object, so they cannot read or write documents.*

***
####




