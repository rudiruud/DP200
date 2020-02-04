201 keywords

## Lambda Architecture

**Cold Path** (Think in tiers with respect to layers)
- **Batch Layer**: Often Azure Storage/ Data Lake
- **Model & Serving Layer**: Often Azure DWH

**Hot Path**
- **Speed Layer**: Often Azure Event Hubs or Stream Analytics Jobs
![0d56478587a8f675ab3cdf7059112e67.png](../_resources/2d4d78b17fa445209a218d588a2dceb7.png)

***
## Kappa Architecture
According to Microsoft reference architectures, Layer 1 serves as a **speed layer** where data can be **accessed easily**. A good fit for this layer would be Cosmos DB. **Layer 2** serves as a **long-term data store**. A good fit for this layer would be Azure DWH.


![8353304279e309a68fd7bce34b4d908c.png](../_resources/c37b040337a945df8fb482271ebeb723.png)

***
A company wants design a solution that supports ingestion and analysis of logs in **real time**. 
- Event Hubs
- Databricks/ OR SAM
- 

***
Behave as an OLTP store -> Azure SQL (In-Memory processing table)
Run queries across petabytes of data -> Azure DWH
Store data in columnar format -> Azure DWH