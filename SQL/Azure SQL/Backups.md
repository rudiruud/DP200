Backups

Azure SQL automatically creates database backups that are stored in Azure Blob GRS with a default retention period of 7 days. This can be managed on singleton databases and elastic pools.

- Every Week: Full backup
- Every 12 hours: Differential backup
- Every 5-10 minutes (based on activity): Transaction log backup.

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-automated-backups?tabs=single-database

***
### Long Term Retention

Long term retention of database backups can be kept in seperated blob storage (up to ten years). 
https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-long-term-backup-retention-configure

