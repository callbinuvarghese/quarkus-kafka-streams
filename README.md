# quarkus-kafka-streams

This project uses Quarkus, the Supersonic Subatomic Java Framework.
https://quarkus.io/guides/kafka-streams

## Build the application in dev mode
mvn clean package -f producer/pom.xml
mvn clean package -f aggregator/pom.xml


### Build and run the application in docker compose
The following builds the producer and aggregator containers
It also brings up a kafka cluster with zookeeper

docker-compose up --build

The following component containers are started by docker compose 
Starting quarkus-kafka-streams_zookeeper_1  ... done
Starting quarkus-kafka-streams_aggregator_1 ... done
Starting quarkus-kafka-streams_producer_1   ... done
Starting quarkus-kafka-streams_kafka_1      ... done




### Inspect the aggregation topic with kafkacat

docker run --tty --rm -i --network ks debezium/tooling:1.1

kafkacat -b kafka:9092 -C -o beginning -q -t temperatures-aggregated
