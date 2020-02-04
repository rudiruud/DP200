Delta API

# Scala Version
In the image below, we create a mock dataframe and save it as a Delta table in some arbritrary path. 
![ed0cbd6fdba5141200472b864b5c5165.png](../_resources/303ad8c8b44044a382fad1bedf85eb3d.png)

Now, we can load the data into df1 as a delta table. This allows us to use the Delta API.
![62d9e77a3640e1c99dea0dfb8161e795.png](../_resources/0e0e58a6076648fcbf12e916dd54ef77.png)

Delta uses versioned parquet files as it's file format. This allows us to query the state of the table either based on a timestamp or the Delta version number. Lets say we update the above dataframe by changing all letters in the Country column to lower case. The current table now looks like this:
![2dc947ddf605c80b91a468091c2089f4.png](../_resources/51b2f9f709294bceae3efe20418d91f1.png)

In Delta we can either provide a version number (versionAsOf) or a timestamp (timestampAsOf) to review a historic snapshot. In this case, we're interested in the initial table:
![484e61bc501332c6e7a4d6cde9f86c1c.png](../_resources/c6c2042ed22c41109f84c8fc0d335daf.png)

## Schema Validation
Lets say we get another similar df but with same different schema. Here everything is same but only the datatype of column id is StringType instead of IntegerType.
![b6e94867de6b9eafcd4cb8431e53a09a.png](../_resources/f80c7f009daa4856b08b36b8caa82d64.png)

It will throw a schema exception on write:
![61731d69b6c3d1a756f47bd2068d7bd3.png](../_resources/bb2a865f5c574728a2fe87052ec88f6f.png)

If there are any new columns in the data we want to append, it will throw an Analysis exception immediately.
![fa01eccff1f2307273527ac75fc5f76b.png](../_resources/9eb2cb21159f482585bcd1a8e3ab60f9.png)


## Missing Data
When there is some missing data and the rest of the schema matches, that field is set to null.
![3536f560f60c77f8dc965b15d2316dc7.png](../_resources/b62b1e686c06453aa0abe84af70bd9df.png)


# Databricks Tutorial

## Creating a Delta table
As described above, first we create a raw table. We will use the PySpark API to read and write data between storage and a Spark dataframe, and SparkSQL API to create a **Delta Table**.

The Bronze table has the delta file format (instead of csv or parwuet) and we can partition it based on some column, with the same best practices as when we would partition Azure SQL or Cosmos DB. When we check the file system path, we will see that the partition created folders for each country. The image below shows the writing of a Spark DF to generic parquet and to Delta. 
![23ef3e221642f951ee61ecb93e27c870.png](../_resources/f66099104b654729909401e7fada4624.png)

At this point, we are already Delta Lake. To add some SQL functionality we can use the SparkSQL API to load the delta files into a **data table**. 
![a7710c096dfcf87b9f59ca76bde4720f.png](../_resources/63d3beb4686c4b97bbee1447c0aab1ab.png)

And now we can query on the table using SQL.
![2025f5250fc53d81c150b67c2788bfc2.png](../_resources/fed21b70a6854600b7ab847896a41853.png)

***
### Appending Data
We can append data using the PySpark API and the append mode. ![50f05133ec85908c20c2c733a657ff10.png](../_resources/70f0a446b7f044859037b9a423fcbc8d.png)

***
## Upserting data
Literally means "UPdate" and "inSERT". It means to atomically either insert a row, or, if the row already exists, UPDATE the row. The focus here is on the atomical part. In normal Spark, UPSERT is not a single atomic operation but TWO operations (UPDATE and INSERT). Running an UPDATE could invalidate data that is accessed by the subsequent INSERT operation.

We now will alter data by changing the values in one of the columns for a specific *CustomerID*. ***Or not, maybe later.***

