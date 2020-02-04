Azure PostreSQL

#### PostgreSQL (Logical) Server 
The PostgreSQL server is a central administration point for one or more databases. The PostgreSQL service in Azure is a managed resource that provides performance guarantees, and provides access and features at the server level.

An Azure Database for PostgreSQL server is the **parent resource** for a database. A resource is a manageable item that's available through Azure. Creating this resource allows you to configure your server instance.

An Azure Database for PostgreSQL server resource is a container with strong lifetime implications for your server and databases. If the server resource is deleted, all databases are also deleted. Keep in mind that all resources belonging to the parent are hosted in the same region.

The server resource name is used to define the server endpoint name. For example, if the resource name is *mypgsqlserver*, then the server name becomes *mypgsqlserver.postgres.database.azure.com*.  



