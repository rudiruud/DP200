Data Lifecycle

#### Container Time To Live
With Time to Live or TTL, Azure Cosmos DB provides the ability to delete items automatically from a container after a certain time period. By default, you can set time to live at the container level and override the value on a per-item basis. After you set the TTL at a container or at an item level, Azure Cosmos DB will automatically remove these items after the time period, since the time they were last modified. Time to live value is configured in seconds. When you configure TTL, the system will automatically delete the expired items based on the TTL value, without needing a delete operation that is explicitly issued by the client application.

