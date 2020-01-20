Azure SQL Introduction

#### Logical Server
When you create your first Azure SQL database, you also create an Azure SQL logical server. Think of a logical server as an administrative container for your databases. You can control logins, firewall rules, and security policies through the logical server. You can also override these policies on each database within the logical server.

For now, you need just one database. *But a logical server enables you to add more later and tune performance among all your databases.*

You have many options to further configure, secure, monitor, and troubleshoot your new database.You can also specify which systems can access your database through the firewall. Initially, the firewall prevents all access to your database server from outside of Azure.

***
#### DTUs versus vCores

- **DTUs**: DTU stands for Database Transaction Unit and is a *combined (fixed) measure of compute, storage, and IO resources*. Because your logical server can hold more than one database, there's also the idea of eDTUs, or elastic Database Transaction Units. This option enables you to choose one price, but allow each database in the pool to consume fewer or greater resources depending on current load.
- **vCores**: vCore gives you greater control over what compute and storage resources you create and pay for. For example, with the vCore model you can increase storage capacity but keep the existing amount of compute and IO throughput.

***
#### Elastic Pools
When you create your Azure SQL database, you can create a SQL elastic pool.

SQL elastic pools relate to eDTUs. They enable you to buy a set of compute and storage resources that are shared among all the databases in the pool. Each database can use the resources they need, within the limits you set, depending on current load.

***
#### Colation
Collation refers to the rules that sort and compare data. Collation helps you define sorting rules when case sensitivity, accent marks, and other language characteristics are important.

