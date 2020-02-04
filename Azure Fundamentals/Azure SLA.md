Azure SLA

- Azure recognizes **Geographies** (e.g. Europe) and Regions (e.g. West-Europe). 
- Each **region** belongs to a single geography and has specific service availability, compliance, and data residency/sovereignty rules applied to it.
- **Availability Zones** are physically separate datacenters within an Azure region.

* * *
#### Region pairs
It's possible that a large enough disaster could cause an outage big enough to affect even two datacenters. That's why Azure also creates region pairs. Each Azure region is always paired with another region within the same geography (such as US, Europe, or Asia) at least 300 miles away. 

* * *
#### Azure SLA's
There are three key characteristics of SLAs for Azure products and services:
- Performance Targets
- Uptime and Connectivity Guarantees
- Service credits

When combining SLAs across different service offerings, the resultant SLA is called a Composite SLA. The resulting composite SLA can provide higher or lower uptime values, depending on your application architecture.

* * *
#### Solution SLA's

Building an efficient and reliable Azure solution requires knowing your workload requirements. You can then select Azure products and services, and provision resources according to those requirements. It's important to understand the Azure SLAs that define performance targets for the Azure products and services within your solution. This understanding will help you create achievable Application SLAs.

