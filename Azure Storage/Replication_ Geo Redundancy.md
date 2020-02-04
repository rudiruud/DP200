Replication/ Geo Redundancy

***
#### Replication
**Redundancy**: When creating a storage account, Azure will automatically maintain a copy of your data within the data center associated with the storage account. This is called **locally-redundant storage (LRS)**, and guards against hardware failure but does not protect you from an event that incapacitates the entire datacenter. You can upgrade to one of the other options such as **zone-redundant storage (ZRS)** or **geo-redundant storage (GRS)** to get replication at different datacenters across the world.

You can change your storage account's replication strategy by using the Azure portal, Azure Powershell, Azure CLI, or one of the Azure Storage client libraries. Changing the replication type of your storage account does not result in down time.
