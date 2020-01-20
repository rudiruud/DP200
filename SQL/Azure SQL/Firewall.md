Firewall

Firewall rules are configured at the server and/or database level, and will specifically state which network resources are allowed to establish a connection to the database. Depending on the level, the rules you can apply will be as follows:

- Server-level firewall rules (Portal, PowerShell, CLI)
   - Allow access to Azure services
   - IP address rules
   - Virtual network rules (can be used in conjunction with VPN Gateway (site to site))
- Database-level firewall rules (TSQL Commands, but very portable)
   - IP address rules

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-firewall-configure

***
### When to use what?
For syncing and restore functionality, it can be usefull to use DB-level firewall rules (since they are scripted instide the database and thus back-upped)
   

