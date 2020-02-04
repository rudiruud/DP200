Clusters

## Cluster modes

Azure Databricks supports two cluster modes: standard and high concurrency. The default cluster mode is standard. 
- Standard clusters are optimal for single person workloads
- High Concurrency clusters are optimized for multiple user workloads due to the following features:
    - Preemption: Proactively preempts Spark tasks from over-committed users to ensure all users get their fair share of cluster time.
    - Fault isolation: Creates an environment for each notebook, effectively isolating them from one another.


## Auto Terminination
The cluster configuration includes an auto terminate setting whose default value depends on whether you are creating a standard or high concurrency cluster:
- Standard clusters are configured to terminate automatically after 120 minutes.
- High concurrency clusters are configured to not terminate automatically.


***
## Autoscaling
When you create a Azure Databricks cluster, you can either provide a fixed number of workers for the cluster or provide a minimum and maximum number of workers for the cluster.


***
## Pooling
When attached to a pool, a cluster allocates its driver and worker nodes from the pool. If the pool does not have sufficient idle resources to accommodate the cluster’s request, the pool expands by allocating new instances from the instance provider. When an attached cluster is terminated, the instances it used are returned to the pool and can be reused by a different cluster.

***
## Permium vs Standard
Databricks premium features AD Credential Passthrough to some services and RBAC for Databricks objects.

***
## Pinning
To keep an interactive cluster configuration even after a cluster has been terminated for *more than 30 days*, an administrator can pin the cluster.

***
## Cluster permissions
Cluster access control allows admins and delegated users to give fine-grained cluster access to other users. Broadly, there are two types of cluster access control:
- Cluster creation permission: Create clusters
- Cluster-level permissions: Start, Manage, Resize a cluster