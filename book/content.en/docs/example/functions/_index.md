---
weight: 20
title: "Functions"
---

# Function Features
## Sequential Messaging
Sequential messaging is one of the key messaging features supported by CatMQ. Sequential messaging follows a FIFO 
(First In, First Out) model, where messages sent earlier are consumed first. CatMQ ensures that messages within a 
Consumer Group are consumed in order. If a message consumption fails, CatMQ will attempt to retry consuming the failed 
message. Only after the specified number of failed retries will it move on to the next message.

## Delayed Messaging
Delayed messaging is primarily designed to meet the needs of scenarios requiring delayed consumption. The unit for 
setting delayed messaging is in seconds. When different consumer groups subscribe to the same topic, you can set 
different delay times for these consumer groups.

## Load Balancing for Consumers and Queues
CatMQ allows dynamic addition or removal of consumers and actual message queues to handle situations where there is 
either too much accumulation of consumption or unexpected crashes of some consumers within a group. CatMQ dynamically 
re-matches the relationship between consumers and queues. Note that if the current number of consumers is greater than 
or equal to the number of queues, simply adding more consumers will not trigger re-balancing.

## Support for One Queue Subscribed by Multiple Consumer Groups
CatMQ supports a queue being simultaneously subscribed to by multiple consumer groups. The consumption of the queue 
by one consumer group does not affect the consumption status of another consumer group. For example, if consumer 
groups A and B both subscribe to queue C, any changes in consumer group B will not impact the consumption status of consumer group A.

## Consumer Progress Adjustment
CatMQ supports real-time dynamic adjustment of the consumption progress for consumer groups. The adjustment takes effect
immediately, and all consumers will start consuming from the new consumption offset. Of course, the new consumption 
offset must be less than the current maximum consumption ID of the message queue. If forcibly set to a new consumption 
offset greater than the maximum ID of the message queue, it will be automatically reset to the maximum ID.

## Message Storage and Scheduled Cleanup
CatMQ uses a database to persist messages, and the database structure design can be referenced in /doc/db. To prevent 
excessive redundant data causing data overflow, queues are created with a default message expiration time. Once the 
message expiration time is reached, messages are automatically cleared.

## Self-Service Operations and Governance
CatMQ features a self-service governance administration console where users can create and manage all topics, 
consumer groups, and consumer offsets. It supports self-service creation and scaling of queues and facilitates 
self-management of relationships between Consumer Groups and Queues.