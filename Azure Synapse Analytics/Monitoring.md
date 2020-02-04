Monitoring

#### Monitoring workloads
**Manually enable** the metrics and diagnostics in Azure DWH to collect the following telemetry:


- **sys.dm_pdw_exec_requests**: Recent request
- **sys.dm_pdw_request_steps**: Detailed execution steps of requests
- **sys.dm_pdw_dms_workers**: Detailed information of works performing executions
- **sys.dm_pdw_waits**: Details on waits encountered
- ***sys.dm_pdw_sql_requests***: Details on workload amongst distributions.

These are views that can be queried in the DWH, but also exported to Azure monitor in the portal.

***
#### How to identify distribution skew bottlenecks

1. Identify your query (Request ID) **dm_pdw_exec_requests**
2. Identify the steps (Step Index) in the query plan **dm_pdw_request_steps**
3. Identify how the query steps on distributions performed **dm_pdw_sql_requests**
4. Investigate data moving across distributions **dm_pdw_dms_worers**

Check the *dm_pdw_waits* to find out what a query is waiting for. 
*** 
Azure SQL Data Warehouse provides a rich monitoring experience within the Azure portal to surface insights to your data warehouse workload. The Azure portal is the recommended tool when monitoring your data warehouse as it provides configurable retention periods, alerts, recommendations, and customizable charts and dashboards for metrics and logs


***
### Database Auditing
By enabling auditing, operations that occur on the database are stored for later inspection or to have automated tools analyze them. This service includes moving the logs to some external storge such as storage, event hub or loga nalaytics. 

Auditing is required when you want to use the extra option threat detection of the advanced data security package.

***
#### Advanced Data Security
Similar to Azure SQL ADS. Consists of:

- Data Discovery and Classification
- Vulnerability Assessment
- Advanced Threat Protection



