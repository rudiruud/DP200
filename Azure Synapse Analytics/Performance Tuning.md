Performance Tuning

There are several areas where you can check performance bottlenecks. 
https://docs.microsoft.com/en-us/azure/sql-data-warehouse/sql-data-warehouse-manage-monitor

***
#### Check Distribution Skew

1. Identify your query (Request ID) **dm_pdw_exec_requests**
2. Identify the steps (Step Index) in the query plan **dm_pdw_request_steps**
3. Identify how the query steps on distributions performed **dm_pdw_sql_requests**
4. Investigate data moving across distributions **dm_pdw_dms_worers**

Check the *dm_pdw_waits* to find out what a query is waiting for.

***
#### Check tempDB
Tempdb is used to hold intermediate results during query execution. High utilization of the tempdb database can lead to slow query performance. Each node in Azure SQL Data Warehouse has approximately 1 TB of raw space for tempdb. It usually happens when there are large data shuffles at the end of a large query plan. Check **dm_pdw_request_steps** for shuffle movements and break up the CTAS *(CREATE TABLE AS SELECT)* in smaller steps if required. 

***
#### Check memory utilization
Memory can be the root cause for slow performance and out of memory issues. Consider scaling your data warehouse if you find SQL Server memory usage reaching its limits during query execution. You need to check memoery usage and pressure per node.

***
#### Check Transaction Logs
The following query returns the transaction log size on *each distribution*. If one of the log files is reaching 160 GB, you should consider scaling up your instance or limiting your transaction size.

***
#### *When using ADLSgen2*, Cache Used percentage
The Gen2 storage architecture automatically tiers your most frequently queried columnstore segments in a cache residing on NVMe based SSDs designed for Gen2 data warehouses. Greater performance is realized when your queries retrieve segments that are residing in the cache. This article describes how to monitor and troubleshoot slow query performance by determining whether your workload is optimally leveraging the Gen2 cache.