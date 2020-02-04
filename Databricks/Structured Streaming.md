Structured Streaming

In Structured Streaming, a data stream is treated as **an unbounded table that is being continuously appended**. This leads to a stream processing model that is very similar to a batch processing model. For this reason, it's often called **micro-batch processing**. You express your streaming computation as a standard batch-like query as on a static table, but Spark runs it as an incremental query on the unbounded input table.

![27a6ad36c39c6b1195c9e58722deaffd.png](../_resources/fcd1f8bc23c249f685875f41a2430469.png)

Consider the input data stream as the input table. Every data item that is arriving on the stream is like a new row being appended to the input table. A query on the input generates a result table. At every trigger interval (say, every 1 second), new rows are appended to the input table, which eventually updates the result table. Whenever the result table is updated, the changed result rows are written to an external sink. The output is defined as what gets written to external storage. Spark can be configured to append the delta or to write the complete table. 

## Demo

To start a streaming query, we only need to specify *spark.readStream* instead of the normal *spark.read* call. In the example below, the option *maxFilesPerTrigger* is used to emulate a stream by looping over a collection of files.
![5c99e7f6a261c2c55d0c7d06f028c782.png](../_resources/22573e83221a4eae99423935374742bc.png)

The API is similar to the normal dataframe API. In the example below, we can simply use the common groupby function. The window function is also common and collects observations in buckets of one hour.
![3344c337735eff62ebce6f678a24f236.png](../_resources/be724d64bf944bb78d993d2869707689.png)

The streaming session is started by specifying an output path and invoking the start() function.
![31260a4523582d1034b0a5ddf464d3bd.png](../_resources/13a80c7ab2ca4d1c871009f8f85361f3.png)

We can stop the session via invoking stop().
![38ef728656fa6a0d8349956c703a126f.png](../_resources/2e7ae76f67af4959b1cdd988cc2590cb.png)


