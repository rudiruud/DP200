DataFrame API

### How data reacts in DataFrames

## Frequently used calls


### Reading and Writing data
*Principle:*
spark.action.options.filetype(path)

*Examples:*
 spark  
  .read
  .option("header", True)
  .option("inferSchema", True)
  .option("timeStampFormat", "yy/mm/dd hh:ss")
  .option("mode", "FAILFAST")
  .option("badRecordsPath", "/tmp/badRecordsPath")
  .csv(path)
  .sample(withReplacement=False, fraction=0.3, seed=3)
<br>  
spark
.write
.mode("overwrite")
.parquet(path)
<br> 
By default, corrupt records are placed in a column called _corrupt_record. These are the records that Spark can't read (e.g. when characters are missing from a JSON string). However, you can specify alternatives in the options for Spark to throw an error upon finding a corrupt record, or to persist corrupt records to an alternate storage via *badRecordsPath*. Semi-structured data works well with hierarchical data and where schemas need to evolve over time. 

json, csv, text, parquet

### Specifying a Schema
Apart from inferring schemas, you can also specify an explicit schema using the StructType and StructFields for each column. Naturally, it's a lot quicker than inferring a schema.

explicit_schema = StructType([
  StructField("ColumnName1", StringType(), True)
  ,StructField("ColumnName2", IntegerType(), True)
  ,StructField("ColumnName3", StringType(), True)
])
df = spark.read.schema(explicit_schema).csv(path)
<br>
Benefits of user defined schemas include:
- **Faster** Avoiding the extra scan of your data needed to infer the schema
- **Flexibility** Providing alternative data types and parsing only the fields you need

### Frequently used dataframe attributes
df.dtypes
df.columns
df.size
df.schema
df.names
df.show()
df.head()
df.take()
<br>

### Selections and filters on dataframes
You can apply select and transformation methods on a dataframe in any order, or chain multiple statements together. 

*Principle:*
df.transformation.action

*Examples:*
DF
.select("*")
.filter((col("code") >= 500) & (col("code") < 600))
.select("HeaderName", "code")
.filter(col("code").isNotNull())
<br>  
DF
.select("firstName", "lastName")
.distinct()


<br>  
*Populair actions:*
dropDuplicates(["column1", "column2"])
explode()
pivot()
cube()
rollup()

### Aggregations
df
.select(hour(from_utc_timestamp(col("time"), "GMT")).alias("hour"))
.groupBy("hour")
.count()  # or max(), min(), avg()
.orderBy("hour")
.show()
<br>  
 df
 .groupBy("age")
 .avg() 
 .show()
 
 ### Cleaning NA
 Records with null values in a DataFrame can be found via:
 *df.na.fill(fill_value)*
 *df.na.drop()*
 *df.dropDuplicates(['columns')*
 
### Adding Columns
Add a column based on input and add new name

df.withColumn(df.firstName.substr(1,3).alias("name"))
df.withColumn("name", df.firstName.substr(1,3))


### Other commands
- filter: Filter based on boolean row based check. Can be used in combination with the method *contains()*
- orderBy
- explode: Loop through all cells that contain an array in a column, and create a new **row** for each value in an array (with all other column values copied)
- alias("NewName") can be executed on any new column
- withColumnRenamed('telePhoneNumber', 'phoneNumber'): Renames a column

