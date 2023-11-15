---
weight: 4
title: "High Availability"
---
# High Availability Design

Let's provide a simple explanation of the overall high availability design:

| Scenario | Impact | Cause |
| --- | --- | --- |
| Individual Broker Failure | No impact | Brokers are stateless, and clients automatically reconnect to other brokers. |
| Individual Message Database Failure | No impact | Master-slave configuration ensures high availability. |
| Metadata Failure | Only affects metadata management functions, no impact on existing production and consumption | Clients and management portal cache metadata. |
| Management Portal (Portal) Failure | Only affects metadata management functions, no impact on existing production and consumption | Clients and management portal cache metadata. |
| Consumer Failure | No impact | CatMQ's dynamic rebalancing will redistribute consumers and queues. |

The implementation of CatMQ's high availability is primarily achieved by building a multi-node cluster and using a leader election mechanism to ensure its own high availability. Specifically, the following strategies are employed:

1. **Leader Election:**
   CatMQ adopts a preemptive leader election approach. If the main master crashes or shows no response for a continuous minute, the system will re-elect a leader to ensure availability. The main master is responsible for synchronizing and updating metadata.

2. **Master-Slave Replication:**
   The main node in CatMQ reads or updates metadata from the database. The secondary node only retrieves metadata from the database while ensuring consistency between the metadata obtained by the main and secondary nodes. This way, even if the main node crashes, the new main node can maintain service availability.

3. **Node Fault Detection:**
   CatMQ uses a heartbeat mechanism for mutual confirmation and status detection. If the main server's heartbeat is not updated within a minute, the cluster will restart the leader election.

4. **Write-Ahead Logging (WAL):**
   CatMQ writes its status to the database during leader election and heartbeat detection. Subsequent operations are performed based on this information, allowing the system to continue operations even if the main node crashes.

5. **Sequential Consistency:**
   Each update operation is assigned a globally unique incremental transaction ID, reflecting the occurrence sequence of all transaction operations, ensuring global sequential consistency for all update operations.

6. **Partitioning:**
   CatMQ divides each topic into multiple partitions. Each partition corresponds to a table in the database, implementing a distributed storage pattern that enhances system concurrency processing capabilities and achieves load balancing.

7. **Replication:**
   Each partition in CatMQ's database table can be set with a corresponding replication table. This increases data redundancy, improves system fault tolerance, and ensures that services can continue even if a database encounters issues.

8. **Database Cluster:**
   CatMQ's configuration metadata and the real-time correspondence between the server and consumer are stored in the database in real-time. Leveraging mature database clustering solutions in the industry can further enhance system availability.

These design and implementation approaches enable CatMQ to achieve high availability and fault tolerance, maintaining service availability even in the face of server failures.