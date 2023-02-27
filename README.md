# kafka-poc

Kafka cluster PoC

## docker-compose

> https://developer.confluent.io/quickstart/kafka-docker/

```
$ docker-compose up -d
$ docker-compose down
```

## topic

```sh
# create topic
docker exec broker \
kafka-topics --bootstrap-server broker:9092 \
             --create \
             --topic quickstart

# write messages to the topic
docker exec --interactive --tty broker \
kafka-console-producer --bootstrap-server broker:9092 \
                       --topic quickstart

# read messages from the topic
docker exec --interactive --tty broker \
kafka-console-consumer --bootstrap-server broker:9092 \
                       --topic quickstart \
                       --from-beginning
```
