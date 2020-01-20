Security

#### RBAC 
Azure Cosmos has RBAC access controlls with predefined roles, such as Reader and Contributor of accounts (but not data) and Owner, etc. 

***
#### Access Keys
Azure Cosmos DB uses two types of keys to authenticate users and provide access to its data and resources.
	
- **Master keys** provide access to all the administrative resources for the database account.
- **Resource tokens**:Used for application resources: containers, documents, attachments, stored procedures, triggers, and UDFs

**Master keys**
Master keys provide access to all the administrative resources for the database account. They provide access to accounts, databases, users, and permissions but *cannot be used to provide granular access to containers and documents.*

In addition to the two master keys for the Cosmos DB account, there are two read-only keys. These read-only keys only allow read operations on the account. *Read-only keys do not provide access to read permissions resources.*

**Resource tokens**
Resource tokens provide access to the application resources within a database. Resource tokens:
- Provide access to specific containers, partition keys, documents, attachments, stored procedures, triggers, and UDFs.
- Are created when a user is granted permissions to a specific resource.
- Are recreated when a permission resource is acted upon on by POST, GET, or PUT call.
- Use a hash resource token specifically constructed for the user, resource, and permission.

You can use a resource token (by creating Cosmos DB users and permissions) **when you want to provide access to resources in your Cosmos DB account to a client that cannot be trusted with the master key (that has account level permissions).** It's the Cosmos equivalent of a DB user with some assigned role. 

https://docs.microsoft.com/en-us/azure/cosmos-db/secure-access-to-data

***
#### Encryption at Rest
With the release of encryption at rest for Cosmos DB, all your databases, media attachments, and backups are encrypted. Your data is now encrypted in transit (over the network) and at rest (nonvolatile storage), giving you end-to-end encryption.

