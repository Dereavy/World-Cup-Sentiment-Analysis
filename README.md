# World-Cup-Sentiment-Analysis
Sentiment analysis of tweets in the context of the 2022 Quatar world cup

## 1. Pipeline schematic
![Pipeline schematic](https://user-images.githubusercontent.com/22829157/212369544-aa56d3ec-3269-4696-bcf8-a61a457baad5.png)

## 1 Kafka Installation:
Kafka installation: https://kafka.apache.org/quickstart

**Start the ZooKeeper service**
In the kafka repository: `cd kafka_2.13-3.3.1`
$ `bin/zookeeper-server-start.sh config/zookeeper.properties`

**Start the Kafka broker service**
In the kafka repository: `cd kafka_2.13-3.3.1`
$ `bin/kafka-server-start.sh config/server.properties`
Once all services have successfully launched, you will have a basic Kafka environment running and ready to use.


## 2 
**Start the Sample Tweets Producer**
`sample_tweets_producer.ipynb`
This will start a service that will stream tweets to kafka.

**Start the Sentiment Analysis Producer**
`sentiment_analysis_producer.ipynb`
This will analyse the tweets and send them to MQTT and save them to a CSV.
Modifications are possible to send to Kafka stream or save with Cassandra.

## 3 Modules:
### Producing a stream of tweets from a pandas dataframe to simulate a real stream of tweets
File: sample_tweets_producer.ipynb
Desc: Kafka Producer service
Usage:
```
streamer = SampleTweetProducer()
streamer.stream()
```
### Create a consumer to watch the tweets on the topic
File: tweets_consumer.ipynb
Desc: Kafka Consumer service
Usage:
```
consumer = TweetConsumer.consumer 
for message in consumer:
            tweet = message.value.decode()
```

### Save the tweets to your database
File: database_service.ipynb
Desc: Saves the tweets to the database or CSV document
Usage:
```
database_service = DatabaseService()
database_service.to_csv(text, polarity, sentiment)
```

### Gets the sentiment of a tweet
File: sentiment_analysis.ipynb
Desc: Carries out the sentiment analysis of tweets
Uses TextBlob to carry out sentiment analysis.
Usage:
```
sentiment_analysis = SentimentAnalysis()
sentiment_analysis.get_sentiment("text to be analysed")
```
### Produce a stream of analysed tweets
File: sentiment_analysis_producer.ipynb
Desc: Producer service for producing the tweets after sentiment-analysis.
The producer to be used can be a kafka producer or mqtt broker.
Usage:
```
sentiment_producer = SentimentAnalysisProducer("MQTT")
sentiment_producer.stream()
```

## Data Visualisation:
Promtail: Consumes the Kafka messages and remote writes to Grafana Loki
For MQTT: https://grafana.com/grafana/plugins/grafana-mqtt-datasource/