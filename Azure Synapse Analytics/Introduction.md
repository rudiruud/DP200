Introduction


#### What is Azure Synapse Analtyics (formerly known as Azure DWH)?
Azure Synapse Analytics is a cloud-based enterprise data warehouse (EDW) that uses massively parallel processing (MPP) to run complex queries across petabytes of data quickly. SQL Data Warehouse is the most appropriate solution when you need to keep *historical* data separate from source transaction systems for performance reasons. The source data might come from other storage mediums, such as network shares, Azure Storage blobs, or a data lake.

Synapse Analytics stores incoming data in relational tables that use *columnar storage*. The format significantly reduces data storage costs and improves query performance. 

***
#### DWU: Resource units
Synapse Analytics separates computation from the underlying storage, so you can scale your computing power independently of data storage. To do this, CPU, memory, and I/O are abstracted and bundled into units of compute scale called data warehouse units (DWUs). A DWU represents an abstract, normalized measure of compute resources and performance. 

Keywords Associated with Synapse Analytics:
* Massive parallel processing
* Historical
* Columnar storage
* Centralized storage for analytics
* Model and Serve










