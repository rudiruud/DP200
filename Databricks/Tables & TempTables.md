Tables & TempTables

### Data tables in Databricks
**managed table** is a table that manages both the data itself as well as the metadata.  In this case, a `DROP TABLE` command removes both the metadata for the table as well as the data itself.  

![7beea3ef1667b8903351196f11a7e92f.png](../_resources/c865dfaecccb4c9aa2d2c4750c98da12.png)


**Unmanaged tables** manage the metadata from a table such as the schema and data location, but the data itself sits in a different location, often backed by a blob store like the Azure Blob Storage. Dropping an unmanaged table drops only the metadata associated with the table while the data itself remains in place.

![7663a409f9f056fee07bce93880fc785.png](../_resources/84323b0ed8d840f2aec64cdfb619ca3d.png)
* Write to an unmanaged table by adding an `.option()` that includes a path. Otherwise, it will be stored as managed table. DESCRIBE EXTENDED tableName can be used to obtain information on the table. 

*Example:*
df.saveAsTable(path)

### Temp views in Databricks
A temp view or temp table allows you to use the SQL API on a dataset but it only lives within your current Spark session. 

*Example:*
df.createOrReplaceTempView("tempTableName")

%sql
SELECT *
FROM tempTableName

