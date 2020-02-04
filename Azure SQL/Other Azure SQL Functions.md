Other Azure SQL Functions

#### Multi-model view for some NoSQL capability
Multi-model databases enable you to store and work with data represented in multiple data formats such as relational data, graphs, JSON/XML documents, key-value pairs, etc.

Azure SQL Database is designed to work with the relational model that provides the best performance in the most of the cases for a variety of general-purpose applications. However, Azure SQL Database is not limited to relational-data only. Azure SQL Database enables you to use a variety of non-relational formats that are tightly integrated into the relational model. You should consider using multi-model capabilities of Azure SQL Database in the following cases:

- You have some information or structures that are better fit for NoSQL models and you don't want to use separate NoSQL database.
- A majority of your data is suitable for relational model, and you need to model some parts of your data in NoSQL style.
- You want to leverage rich Transact-SQL language to query and analyze both relational and NoSQL data, and integrate it with a variety of tools and applications that can use SQL language.

https://docs.microsoft.com/en-us/sql/relational-databases/json/json-data-sql-server?view=sql-server-ver15
***
#### In-Memory technologies

By using In-Memory technologies in Azure SQL Database, you can achieve performance improvements with various workloads:

- Transactional (online transactional processing (OLTP)) where most of the requests read or update smaller set of data (for example, CRUD operations). E.g. real time chats.
- Analytic (online analytical processing (OLAP)) where most of the queries have complex calculations for the reporting purposes, with a certain number of queries that load and append data to the existing tables (so called bulk-load), or delete the data from the tables.
- Mixed (hybrid transaction/analytical processing (HTAP)) where both OLTP and OLAP queries are executed on the same set of data.

In-memory technologies can improve performance of these workloads by keeping the data that should be processed into the memory, using native compilation of the queries, or advanced processing such as batch processing and SIMD instructions that are available on the underlying hardware.

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-in-memory
***
**Get insight in data evolutions with Temporal Tables**
Temporal Tables are a new programmability feature of Azure SQL Database that allows you to track and analyze the full history of changes in your data, without the need for custom coding. Temporal Tables keep data closely related to time context so that stored facts can be interpreted as valid only within the specific period. This property of Temporal Tables allows for efficient time-based analysis and getting insights from data evolution.

***
### When to use what?
By default, don't pick Azure SQL for its JSON/ NoSQL capabilities but resort to CosmosDB instead. Consider in-memory processing for transactional/ ORD purposes.
