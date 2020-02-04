Joins and Lookup tables

A common use case in ETL jobs involves joining new data to either lookup tables or historical data.  A lookup table is small table often used for referencing commonly used data such as mapping cities to countries. Traditional databases join tables by pairing values on a given column. When all the data sits in a single database, it often goes unnoticed how computationally expensive row-wise comparisons are.  When data is distributed across a cluster, the expense of joins becomes even more apparent.

**A standard (or shuffle) join** moves all the data on the cluster for each table to a given node on the cluster. This is expensive not only because of the computation needed to perform row-wise comparisons, but also because data transfer across a network is often the biggest performance bottleneck of distributed systems.

By contrast, **a broadcast join** remedies this situation when one DataFrame is sufficiently small. A broadcast join duplicates the smaller of the two DataFrames on each node of the cluster, avoiding the cost of shuffling the bigger DataFrame.

<img src="https://files.training.databricks.com/images/eLearning/ETL-Part-2/shuffle-and-broadcast-joins.png" style="height: 400px; margin: 20px"/>

By default, Spark tries to use broadcast joins. There are some configurations possible and details on the join type can be found using *df1.join(df2, "columnname").explain()*



### API 
*df_left.join(df_right, "column_name", "left")*