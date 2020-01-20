Default High Availability

This section is on the default out-of-the-box high availability architecture of a single SQL DB. It does **not** discuss **Geo-Replication** or **Failover Groups** which both increase the high-availability. 

There are two default high-availability architectural models that are used for the different tier options for the Azure SQL Database. 
- Standard availability model that is based on a separation of compute and storage. It relies on high availability and reliability of the remote storage tier. 
- Premium availability model that is based on a cluster of database engine processes. It relies on the fact that there is always a quorum of available database engine nodes.

#### Standard availability model
Azure SQL **Basic** (eDTU), **Standard** (eDTU), **General** (vCore) tiers use the standard availability model which includes **two layers**:

- A **stateless compute layer** that runs the sqlservr.exe process and contains only transient and cached/ memory data. This stateless node is operated by Azure Service Fabric that performs failover to another node if necessary.
- A **stateful data layer** with the database files (.mdf/.ldf) that are stored in Azure Blob storage *(with blob storage  built-in data Geo-Redudancy)*. It guarantees that every record in the log file or page in the data file will be preserved even if SQL Server process crashes. (Note that the compute layer is not geo-redundant).

Whenever the database engine or the operating system is upgraded, or a failure is detected, Azure Service Fabric will move the stateless SQL Server process to another stateless compute node with sufficient free capacity.

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-high-availability

#### Premium Availability Model
Azure SQL **Premium** (eDTU) and **Business Critical** tiers 
use a Premium availability model, which integrates compute resources (SQL Server Database Engine process) and storage (locally attached SSD) on a **single node**. High availability is achieved by replicating both compute and storage to additional nodes creating a three to four-node cluster in what is called an *always on availability group.*

***
### Other: Hyperscale
The Hyperscale service tier architecture is a distributed system that is even more available.
https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-high-availability


***
### SQL Managed Instance/ SQL on a Virtual Machine
These SQL platforms do not have the high availability features described above.  

