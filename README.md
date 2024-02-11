# kafka

## docker-compose

```sh
docker pull --tls-verify=false docker.io/confluentinc/cp-zookeeper:latest
docker pull --tls-verify=false docker.io/confluentinc/cp-kafka:latest
docker pull --tls-verify=false docker.io/provectuslabs/kafka-ui:latest

docker-compose up

$ docker-compose logs kafka | grep -i started
[2024-02-11 08:39:14,084] DEBUG [ReplicaStateMachine controllerId=1] Started replica state machine with initial state -> HashMap() (kafka.controller.ZkReplicaStateMachine)
[2024-02-11 08:39:14,101] DEBUG [PartitionStateMachine controllerId=1] Started partition state machine with initial state -> HashMap() (kafka.controller.ZkPartitionStateMachine)
[2024-02-11 08:39:14,152] INFO [KafkaServer id=1] started (kafka.server.KafkaServer)
```

__kafka-ui__

http://localhost:9080

```
> Configure new cluster'
Cluster name: kafka-docker
Bootstrap Servers *
Host: kafka
Port: 9092
```

## Tools

### kcat

__macOS__

```
brew install kcat
```

__docker__

```sh
alias kcat='docker run --rm -ti --network=host docker.io/edenhill/kcat:1.7.1'
```

```sh
$ kcat -b localhost:29092 -L
Metadata for all topics (from broker 1: localhost:29092/1):
 1 brokers:
  broker 1 at localhost:29092 (controller)
 0 topics:
```

### kafka-ui

```sh
alias kui='docker run --rm -it --network=host -p 8080:8080 -e DYNAMIC_CONFIG_ENABLED=true docker.io/provectuslabs/kafka-ui'
```

```
$ kui

> Configure new cluster'
Cluster name: kafka-local
Bootstrap Servers *
Host: localhost
Port: 29092
```

## Notes

- https://hub.docker.com/r/bitnami/kafka
- https://github.com/provectus/kafka-ui
- [My top 5 tools to manage/develop with Apache Kafka](https://needablackcoffee.medium.com/my-top-5-tools-to-manage-develop-with-apache-kafka-2e6790a88ef2)
- [Recommend a Simple Kafka UI Tool](https://dev.to/dariusx/recommend-a-simple-kafka-ui-tool-5gob)
- [Overview of UI Tools for Monitoring and Management of Apache Kafka Cluster](https://towardsdatascience.com/overview-of-ui-tools-for-monitoring-and-management-of-apache-kafka-clusters-8c383f897e80)
