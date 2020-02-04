Encryption

#### TLS
Sql Server enforces encryption (SSL/TLS) at all times for all connections. This ensures all data is encrypted "in transit" between the client and server irrespective of the setting of Encrypt or TrustServerCertificate in the connection string.

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-dynamic-data-masking-get-started

***
### Transparant Data Encryption
In Azure, all newly created SQL databases are encrypted by default and the database encryption key is protected by a built-in server certificate. Certificate maintenance and rotation are managed by the service and requires no input from the user. *Customers who prefer to take control of the encryption keys can manage the keys in Azure Key Vault.* 

**TDE Key management with Azure Key Vault**

Bring Your Own Key (BYOK) support for Transparent Data Encryption (TDE) allows customers to take ownership of key management and rotation using Azure Key Vault, Azure’s cloud-based external key management system. If the database's access to the key vault is revoked, a database cannot be decrypted and read into memory. Azure Key Vault provides a central key management platform, leverages tightly monitored hardware security modules (HSMs), and enables separation of duties between management of keys and data to help meet security compliance requirements.

https://docs.microsoft.com/nl-nl/azure/sql-database/transparent-data-encryption-azure-sql?tabs=azure-portal

***
#### Always Encrypted
Always Encrypted is a feature designed to protect sensitive data stored in specific database columns from access (for example, credit card numbers, national identification numbers, or data on a need to know basis). This includes database administrators or other privileged users who are authorized to access the database to perform management tasks, but have no business need to access the particular data in the encrypted columns. The data is always encrypted, *which means the encrypted data is decrypted only for processing by client applications with access to the encryption key*. The encryption key is never exposed to SQL and can be stored either in the Windows Certificate Store or in Azure Key Vault.

Randomized or Deterministic?
- Deterministic encryption always generates the same encrypted value for any given plain text value. Using deterministic encryption allows point lookups, equality joins, grouping and indexing on encrypted columns. 
- Randomized encryption uses a method that encrypts data in a less predictable manner. Randomized encryption is more secure, but *prevents searching, grouping, indexing, and joining on encrypted columns.*

Always encrypted is usefull to hide data away from adminsitrators. For example:
- The customer wants to hire an external vendor to administer SQL Server. 
- When using Azure SQL, store Always Encrypted keys in a trusted key store hosted on-premises, to ensure Microsoft cloud administrators have no access to sensitive data.

https://docs.microsoft.com/nl-nl/azure/sql-database/sql-database-always-encrypted-azure-key-vault?tabs=azure-powershell

***
### When to use what?
By default, use TLS for data in movement and TDE for data at rest encryption. When there are specific situations regarding key management, you probably want to look for always-encrypted. Determine whether there requirements that render (always encrypted) randomized encryption infeasible. 

***
#### Advanced Data Security
ADS contains a set of advanced SQL security capabilities, including data discovery & classification (intelligent dynamic masking), vulnerability assessment (DB scan permissions, vulnerabilities), and Advanced Threat Protection (SQL command scans, e.g. sql injection monitor).

- Data Discovery and Classification
- Vulnerability Assessment
- Advanced Threat Protection
