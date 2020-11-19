# quarkus-kafka-streams

This project uses Quarkus, the Supersonic Subatomic Java Framework.

## Build the application in dev mode
mvn clean package -f producer/pom.xml
mvn clean package -f aggregator/pom.xml


### Build and run the application in docker compose
The following builds the producer and aggregator containers
It also brings up a kafka cluster with zookeeper

docker-compose up --build


### Inspect the aggregation topic with kafkacat

docker run --tty --rm -i --network ks debezium/tooling:1.1

kafkacat -b kafka:9092 -C -o beginning -q -t temperatures-aggregated
