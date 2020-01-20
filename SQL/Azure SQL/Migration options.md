Migration options


A database migration can be online (seamless) or offline (db downtime). Both options are possible with the below migration paths. 

### Automated assessment/ migration:
- Tool: **Database Migration Assistant** does assessments and recommendations based on your current SQL Server solution.
- Tool: **Database Migration Service** does a DMA and then migrates your solution to Azure SQL or SQL Managed Instance (needs VPN)

### Manual assessment/ migration:
- Manual: Via SSMS with the SQL Database migration wizzard
- Manual: Via an SSMS export (BACPAC file) which is then moved to Blob Storage and imported in an Azure SQL DB
- Setting: **Transactional Replication** syncs two SQL databases (cloud/ cloud or prem/ cloud) and can also be used to migrate a DB. It first creates a seed and then updates transactions as they come. Can be used to isolate an on-prem DB and allow user-access to a replicated cloud DB. 

### Managed Instance
Managed Instance is highly backwards compatible with SQL Server Engine, including SQL Agent (SQL  native SQLCMD job scheduler), Cross DB transactions, Native Backups and DB mails. It has the regular security options (TLS, TDE, RBAC with/without AAD) plus row level security. 