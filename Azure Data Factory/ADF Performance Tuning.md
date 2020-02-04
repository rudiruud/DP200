ADF Performance Tuning



ADF offers a serverless architecture that allows parallelism at different levels, which allows developers to build pipelines to fully utilize your network bandwidth as well as storage IOPS and bandwidth to maximize data movement throughput for your environment. This means the throughput you can achieve can be estimated by measuring the minimum throughput offered by the source data store, the destination data store, and network bandwidth in between the source and destination. 

The following steps can be done if the source data store, the network in between, or the destination data store has reached its bottleneck:

1. Increase Data Integration Units for the activity(s) - e.g., adding more resources to the pipeline. This works best when using Azure IR. 
2. If adding DIUs does not accelerate the pipeline, consider to create concurrent copy activities (using loops in your main pipeline). Add parrelel copies (increase the number of threads per copy activity)

https://docs.microsoft.com/en-us/azure/data-factory/copy-activity-performance
***
**Set Staged Copy**
To improve performance, you can use staged copy to compress the data on-premises so that it takes less time to move data to the staging data store in the cloud. Then you can decompress the data in the staging store before you load into the destination data store.
- Reduces data size traveling through network
- Allows the use of more optimized tools such as Spark, Polybase
- Allows the use of broadly used HTTPS ports instead of MSSQL

