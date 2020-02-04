Delta Lake

Delta Lake 
- Bronze (RAW CSV's, JSON's, TXT)
- Silver (Filtered, Cleaned & Augmented data version. First queryable structure of data). Acts like a checkpoint from which to rerun a gold data-set. Comparable to Curated data layer set.
- Gold (Business level aggregates. Often built for specific use cases).

Delta Lake bronze just listens for CDC/ Batch processes and you can sync other tables (Silver, Gold) from that. Delta Lake removes the enrichment (Failed, Success, Busy) overhead from you through ACID transactions. 

***
### Writing data
You can write a dataframe in Delta format which is basically a transaction logged parquet file written to the specified path. 

    dataframe.write.format("delta").path?("/home/db/")

***
Non-spark Python code wordt gerund op de driver node.
***

