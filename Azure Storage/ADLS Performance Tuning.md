ADLS Performance Tuning

#### Tuning Ingestion
When ingesting data from a source system to Data Lake Storage Gen2, it is important to consider that the source hardware, source network hardware, and network connectivity to Data Lake Storage Gen2 can be the bottleneck.
- Source Hardware
- Source Network connectivitiy
- Network connectivity

#### File size Tuning

Typically, analytics engines such as HDInsight and Azure Data Lake Analytics have a per-file overhead. If you store your data as many small files, this can negatively affect performance. **In general, organize your data into larger sized files for better performance (256MB to 100GB in size).**

***
#### IO Tuning
You can have a job that reads or writes as much as 100MB in a single operation, but a buffer of that size might compromise performance. To optimize performance, try to keep the size of an I/O operation between 4MB and 16MB.

***
