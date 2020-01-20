Backups

Azure Cosmos DB automatically takes backups of your data at regular intervals. The automatic backups are taken without affecting the performance or availability of the database operations. All the backups are stored separately in a storage service, and those backups are globally replicated for resiliency against regional disasters. The automatic backups are helpful in scenarios when you accidentally delete or update your Azure Cosmos account, database, or container and later require the data recovery.

- Azure Cosmos DB automatically takes a backup of your database every 4 hours and at any point of time, only the latest 2 backups are stored. However, if the container or database is deleted, Azure Cosmos DB retains the existing snapshots of a given container or database for 30 days.
- Azure Cosmos DB stores these backups in Azure Blob storage whereas the actual data resides locally within Azure Cosmos DB, but is also stored with Azure Storage GRS enabled.


