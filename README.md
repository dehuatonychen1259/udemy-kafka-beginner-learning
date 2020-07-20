# udemy-kafka-beginner-learning

Learning the Kafka Beginner's course on Udemy. \
Will put down important commands here so that i can remember them.

## Starting Up kafka

```
zookeeper-server-start.sh config/zookeeper.properties
```
```
kafka-server-start.sh config/server.properties
```


## Kafka Topics

Create a topic with 3 partitions and 2 Replication factor, note replication factor must be equal to or less than number of brokers
```
kafka-topics.sh --zookeeper 127.0.0.1:2181 --topic first_topic --create --partitions 3 --replication-factor 2
```

List all topics for a particular zookeeper IP Port
```
kafka-topics.sh --zookeeper 127.0.0.1:2181 --list
```

How to describe a topic to more lengths
```
kafka-topics.sh --zookeeper 127.0.0.1:2181 --topic first_topic --describe
```

How to delete a topic
```
kafka-topics.sh --zookeeper 127.0.0.1:2181 --topic second_topic --delete
```

## Kafka Producer

How to connect to Kafka and produce some messages, you'll have to input your own messages with this command
```
kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic first_topic
```

How to connect to Kafka and produce some messages with another property such as acks
```
kafka-console-producer.sh --broker-list 127.0.0.1:9092 --topic first_topic --producer-property acks=all
```
Note if you send a message to a topic that hasn't been created yet, Kafka will create one for you with an error LEADER NOT AVAIALBLE. What happens though is that a topic is created for you with a partition of 1 and a replication of 1 which is usually not what you would want.  By default you can change the server.properties file in order to change the default number of partitions that are created if a topic does not exist.

## Kafka Consumer

This will start the Kafka consumer, note that the messages are only being received at the point of this program run
```
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic first_topic
```

Start the consumer, but also output all producer messages that have been sent to the topic
```
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic first_topic --from-beginning
```

## Kafka Consumers in a Group

This starts a consumer in a group, if multiple tabs are created with this same command, then producers will send messages to only one of the consumers in that consumer group.  Rebalance and share the load of messages.  If a tab is closed then we will repartition and send it to the live tabs.  If you use --from-beginning twice, the second run will not produce messages as the offsets have been committed. If all tabs are closed and you rerun when new messages are produced, it will list them all.
```
kafka-console-consumer.sh --bootstrap-server 127.0.0.1:9092 --topic first_topic --group my-first-application
```

## Kafka Consumer Groups

List all consumer groups, some with a random generated number.
```
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --list
```

Lists all the topics for that consumer group, the logs, offsets, and lag of data read
```
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --describe --group my-first-application
```

## Reset Offsets

You can choose where you can start again by period, earliest, latest,, shift by, from file, to current.  If you run the thing again --from-beginning you should see all the messages again.  
```
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --grou- my-first-application --reset-offsets --to-earliest --execute --topic first_topic
```

You can shift forward and backwards for your consumer groups.  This is working for all partitions and not just 1.
```
kafka-consumer-groups.sh --bootstrap-server localhost:9092 --grou- my-first-application --reset-offsets --shift-by -2 --execute --topic first_topic
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```

```
```
