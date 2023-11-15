---

weight: 13
title: "Concept"
---

# Introduction to Basic Concepts

This page will introduce the fundamental concepts involved in CatMQ to help users understand CatMQ better.

## Topic
A topic represents an aggregation of a certain type of message, used to distinguish different business messages. The relationship between topics and messages is one-to-many logic, and it is the smallest unit of message subscription in CatMQ.

In topic-based systems, messages are published to topics or named channels. Consumers receive all messages on the topics they subscribe to, and producers define the categories of messages subscribers subscribe to. This is a basic conceptual model, and in actual applications, the structure can be more complex. For example, to support high concurrency and horizontal scaling, the intermediate message topics need to be partitioned. The same topic may have multiple producers, and the same message may have multiple consumers, with load balancing between consumers.

## Message
A message is the smallest unit of data transfer in CatMQ. Producers wrap business data into messages and send them to the server. The server delivers messages to consumers for consumption according to the relevant semantics.

## Consumer Group
A consumer group is an abstract concept with multiple consumers under it. A consumer group collectively subscribes to a topic. Messages are dynamically allocated to different consumers based on a set algorithm, enhancing system fault tolerance and scalability.

## Producer/Consumer
Producers are responsible for producing messages, typically managed by the business side. Message producers send messages to the server (Broker) of the message system.
Consumers are responsible for consuming messages, usually downstream businesses, retrieving messages from the server of the consumption system.

## Queue
A queue is where messages are actually stored, and it is the smallest unit of message storage. All topics in CatMQ are composed of multiple queues.

## Message Offset (MessageQueueOffset)
Message offset records the position of a message in the queue. Since the system persists information, old messages do not disappear after consumption. The system automatically records the latest message consumption position, and the next time messages are consumed, they start from this offset.

## Message Tag (MessageTag)
Message tags are fine-grained consumption classification attributes provided by CatMQ. Consumers can control messages more finely based on MessageType.

## Message Subscription (Subscribe)
Message subscription is the rule and status configuration for consumers to receive and process messages. After subscribing to a topic, messages from that topic will be sent to the consumer.

## Broker
The basic operational unit of CatMQ, a stateless entity that can easily scale horizontally, go online, or offline.

## Portal
The front-end operational management interface of CatMQ. Through visual operations, access control, and other functions, users can easily and intuitively manage the metadata information of CatMQ.






