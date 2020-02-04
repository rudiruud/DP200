Data Protection

### Restore a DWH
A data warehouse restore is a new data warehouse that is created from a restore point of an existing or deleted data warehouse. This means that any old security, firewall and configurations need to be applied to the new datawarehoues before it can be used properly.

As restore point, an automatic or user-defined restore point can be used. 

### Automatic Restore points
SQL Data Warehouse takes snapshots of your data warehouse throughout the day creating restore points that are available for seven days. This retention period cannot be changed. SQL Data Warehouse supports an **eight-hour recovery point objective (RPO)**. 

### User defined restore points
This feature enables you to manually trigger snapshots to create restore points of your data warehouse before and after large modifications. This capability ensures that restore points are logically consistent, which provides additional data protection in case of any workload interruptions or user errors for quick recovery time. 

**User-defined restore points are available for seven days and are automatically deleted on your behalf.** You cannot change the retention period of user-defined restore points. 42 user-defined restore points are guaranteed at any point in time so they must be deleted before creating another restore point.


***
#### GeoBackups
SQL Data Warehouse performs a geo-backup once per day to a paired data center (RPO of 1 day).