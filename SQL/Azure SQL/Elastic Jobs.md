Elastic Jobs

Elastic jobs is a cloud-version of the on-premise SQL agent. You can orchestrate jobs accross multiple databases, servers and pools. Usually, this consists of some T-SQL script that performs DB maintenance.

It uses a SQL DB as a job agent. Inside the *job database*, you need to configure which (group of) database(s) is your *target group*, and what script it needs to run. It can also pull back some results.

Jobs can be run from the portal, PS or from the job agent DB.

#### Credentials
Jobs use database scoped credentials to connect to the databases specified by the target group upon execution. If a target group contains servers or pools, these database scoped credentials are used to connect to the master database to enumerate the available databases.

https://docs.microsoft.com/nl-nl/azure/sql-database/elastic-jobs-overview