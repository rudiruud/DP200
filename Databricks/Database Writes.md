Database Writes

### Partitions and Slots

Writing to a database in Spark differs from other tools largely due to its distributed nature. There are a number of variables that can be tweaked to optimize performance, largely relating to how data is organized on the cluster. Partitions are the first step in understanding performant database connections.

**A partition is a portion of your total data set,** which is divided into many of these portions so Spark can distribute your work across a cluster. 

The other concept needed to understand Spark's computation is a slot (also known as a core). **A slot/core is a resource available for the execution of computation in parallel.** In brief, a partition refers to the distribution of data while a slot refers to the distribution of computation.

    As a general rule of thumb, the number of partitions should be a multiple of the number of cores. For instance, with 5 partitions and 8 slots, 3 of the slots will be underutilized. With 9 partitions and 8 slots, a job will take twice as long as it waits for the extra partition to finish, while the other slots are still not utilized.
    
***   
### Managing Partitions/ Connections
In the context of JDBC database writes, **the number of partitions determine the number of connections used to push data through the JDBC API.** This is in contrast to reading from databases, where the number of partitions is defined in the database call. There are two ways to controll this parallelism:  

| Function | Transformation Type | Use | Evenly distributes data across partitions? |
| :----------------|:----------------|:----------------|:----------------| 
| `.coalesce(n)`   | narrow (does not shuffle data) | reduce the number of partitions | no |
| `.repartition(n)`| wide (includes a shuffle operation) | increase the number of partitions | yes |

*Example:*
- Getting the number of partitions: *spark.conf.set("spark.sql.shuffle.partitions")*
- Setting the number of partitions: *spark.conf.set("spark.sql.shuffle.partitions", "8")*

Alternatively, you can view it through the notebooks. 
***
###



