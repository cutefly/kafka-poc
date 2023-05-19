# kafka-poc

Kafka cluster PoC

## docker-compose

> https://developer.confluent.io/quickstart/kafka-docker/

```
$ docker-compose up -d
$ docker-compose down
```

### kafka exporter

```
# race condition 이슈로 docker compose 내에서 사용 불가
$ docker run -ti --rm --name kafka-exporter -p 9308:9308 --network 3rdparty bitnami/kafka-exporter --kafka.server=broker:29092

http://localhost:9308/
```

## topic

```sh
# create topic
docker exec broker \
kafka-topics --bootstrap-server broker:9092 \
             --create \
             --partitions 3 \
             --replication-factor 1 \
             --if-not-exists \
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

### create topic with options

```
kafka-topics --create --topic exam --partitions 3 --replication-factor 1 --if-not-exists --bootstrap-server broker:29092
```
