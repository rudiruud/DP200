Platform options

There are several platforms on which SQL Server can be deployed, depending on the needs. Some of these platforms also originate from specific migration/ legacy requirements. 

### Deployment options
- Azure SQL
    - Azure SQL (Logical Server with single database)
    - Azure SQL Elastic Pool (with one or more logical servers)
- Azure SQL Managed Instance (Single database *with a vCore model* that is highly backwards compatible with on-premise SQL Server and hyperscalable)
- Azure SQL on a VM (if you only want to purely outsource to IaaS or need complete server level control)

***
### Azure SQL: eDTU vs vCores

- eDTU are simple service packages of CPU/ Storage
  - Basic <2GB
  - Standard <1TB
  - Premium <4TB
- vCores allow you to customise CPU and Storage to specific needs. 
  - General <4TB
  - Business Critical <4TB, with high availability options (replicas + read-specific replica)
  - Hyperscale <100TB

***
### Managed Instance
Managed Instance is highly backwards compatible with SQL Server Engine, including SQL Agent (SQL  native SQLCMD job scheduler), Cross DB transactions, Native Backups and DB mails. It has the regular security options (TLS, TDE, RBAC with/without AAD) plus row level security. 

***
### What to use when?
- Azure SQL eDTU is the default deployment option. Azure SQL vCores if you want to do specific workloads that only require either volume or compute power. 
    - Choose a specific depending when there are certain volume requirements, or based on requirements for (un-)seperation of compute and storage tiers (see default high availability)
    - Elastic pools if you need to pool resources amongst multiple databases
- SQL Managed Instance if you want full backwards compatability.
- SQL on a VM if you want full server control