# World-Cup-Sentiment-Analysis
Sentiment analysis of tweets in the context of the 2022 Quatar world cup

## 1. Pipeline creation
### 1.1 Kafka Installation:
Kafka installation: https://kafka.apache.org/quickstart

**Start the ZooKeeper service**
$ bin/zookeeper-server-start.sh config/zookeeper.properties

**Start the Kafka broker service**
$ bin/kafka-server-start.sh config/server.properties
Once all services have successfully launched, you will have a basic Kafka environment running and ready to use.

## Producing a stream of tweets from a pandas dataframe to simulate a real stream of tweets
file: sample_tweets_producer.ipynb
desc: Kafka Producer service

##
file: tweets_consumer.ipynb
desc: Kafka Consumer service

##
file: database_service.ipynb
desc: Saves the tweets to the database

##
file: sentiment_analysis.ipynb
desc: Kafka Producer service

##
file: sentiment_analysis_producer.ipynb
desc: Kafka Producer service

## Data Visualisation:
Promtail: Consumes the Kafka messages and remote writes to Grafana Loki
