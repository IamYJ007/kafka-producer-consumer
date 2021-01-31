# kafka-producer-consumer
Using spring boot project send and receive kafka messages

# kafka-publisher
Apache Kafka Publisher Example using SpringBoot

# start zookeeper.start bat file like below
zookeeper-server-start.bat C:\Users\yjayara\Downloads\kafka_2.12-2.3.1\config\zookeeper.properties

# start kafka server
kafka-server-start.bat C:\Users\yjayara\Downloads\kafka_2.12-2.3.1\config\server.properties

# Create Topic:
kafka-topics.bat --create --zookeeper localhost:2181\kafka --replication-factor 1 --partitions 1 -topic demo

kafka-topics.bat --create --zookeeper localhost:2181 --replication-factor 1 --partitions 1 -topic demo <--- correct

# Produce a message
kafka-console-producer.bat --broker-list localhost:9092 --topic demo

# Consume a message
kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic demo


kafka-topics.bat --list --zookeeper localhost:2181

kafka-topics.bat --describe  --zookeeper localhost:2181 --topic demo

listeners=PLAINTEXT://53.88.124.91:9092

Connection to node -1 could not be established/Connection to node 0 could not be established. Broker may not be available -> for this error -> delete-tmp-logs in c:\tmp\kafka-logs


https://kafka.apache.org/protocol.html#protocol_network

//Messages
Kafka Messages are byte arrays that can store any object in any format. As said before, all Kafka messages are organized into topics. If you wish to send a message you send it to a specific topic and if you wish to read a message you read it from a specific topic.

//Network
Kafka uses a binary protocol over TCP. The protocol defines all APIs as request response message pairs. All messages are size delimited and are made up of the following primitive types.

//Kafka brokers communicate
When communicating with a Kafka cluster, all messages are sent to the partition's leader. The leader is responsible for writing the message to its own in sync replica and, once that message has been committed, is responsible for propagating the message to additional replicas on different brokers

//Zookeeper
Kafka (even in most recent version) will not work without Zookeeper. Kafka uses Zookeeper for the following: Electing a controller. The controller is one of the brokers and is responsible for maintaining the leader/follower relationship for all the partitions

//offset
The offset is a simple integer number that is used by Kafka to maintain the current position of a consumer. That's it. The current offset is a pointer to the last record that Kafka has already sent to a consumer in the most recent poll. So, the consumer doesn't get the same record twice because of the current offset

//binary protocol
A binary protocol is a protocol which is intended to be read by a machine rather than a human being, as opposed to a plain text protocol such as IRC, SMTP, or HTTP/1.1. Binary protocols have the advantage of terseness, which translates into speed of transmission and interpretation.
