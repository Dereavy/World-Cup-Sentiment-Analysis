# World-Cup-Sentiment-Analysis
Sentiment analysis of tweets in the context of the 2022 Quatar world cup

## 1. Pipeline creation
![Pipeline schematic](https://user-images.githubusercontent.com/22829157/212369544-aa56d3ec-3269-4696-bcf8-a61a457baad5.png)

### 1.1 Kafka Installation:
Kafka installation: https://kafka.apache.org/quickstart

**Kafka with ZooKeeper**
Run the following commands in order to start all services in the correct order:

**Start the ZooKeeper service**
$ bin/zookeeper-server-start.sh config/zookeeper.properties
Open another terminal session and run:

**Start the Kafka broker service**
$ bin/kafka-server-start.sh config/server.properties
Once all services have successfully launched, you will have a basic Kafka environment running and ready to use.

### 1.2 Create a topic to store the events
We need to create a topic to store new tweets that get streamed.

### 1.3 Write events into the topic

## 2. Spark Streaming and Sentiment analysis
TBD
