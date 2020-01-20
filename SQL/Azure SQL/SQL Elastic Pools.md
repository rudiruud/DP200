SQL Elastic Pools

#### Elastic Pools
SQL elastic pools are a resource allocation service used to scale and manage the performance and cost of a group of Azure SQL databases. Elastic pools allow you to purchase resources for the group. You set the amount of resources available to the pool, add databases to the pool, and set minimum and maximum resource limits for the databases within the pool.

SQL elastic pools are ideal when you have several SQL databases that have a low average utilization, but have infrequent, high utilization spikes. 

##### When is a pool cost effective?
The general guidance is, if the combined resources you would need for individual databases to meet capacity spikes is more than 1.5 times the capacity required for the elastic pool, then the pool will be cost effective.

At a minimum, it is recommended to add at least two S3 databases or fifteen S0 databases to a single pool for it to have potential cost savings.

Depending on the performance tier, you can add up to 100 or 500 databases to a single pool.

**Costs are determined by Storage and CPU (or eDTU, which is the cominbation of these 2**



***
#### Configuration options

- Set min- and max performance limits per database in a pool
- Change the Service Tier (or switch between eDTU/ vCore)
- Add or remove databases

***
#### Monitoring Elastic Pools
In essense, you'd generally monitor the pool resource consumption and focus less on the individual databases. You can set some alerts when performance boundaries on the pool are exceded. 




