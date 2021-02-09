# Kafka - Multinode cluster setup using docker

## Environment Setup

1.  ### Docker installation

    Follow the official documentation of [docker](https://docs.docker.com/engine/install/)
    to setup docker on your machine.
    After installation of docker.

    ```bash
    # start docker service
    sudo service docker start

    # docker version
    docker -v

    # docker-compose version
    docker-compose -v
    ```

1.  ### Spinnig kafka-cluster

    ```bash
    # clone repository
    git clone https://github.com/dhananjay5544/kafka-setup.git
    cd kafka-cluster-setup

    # start kafka cluster
    docker-compose up -d
    ```

> Basic commands for kafka

### Create topic

```bash
kafka-topics \
 --bootstrap-server localhost:19092,localhost:29092,localhost:39092 \
 --topic test-topic \
 --create \
 --replication-factor 3 \
 --partitions 6
```

### Describe topic

```bash
kafka-topics \
 --bootstrap-server localhost:19092,localhost:29092,localhost:39092 \
 --topic test-topic \
 --describe
```

### Start console-producer

```bash
kafka-console-producer \
   --topic test-topic \
   --broker-list localhost:19092,localhost:29092,localhost:39092
```

### Start console-consumer

```bash
kafka-console-consumer \
   --topic test-topic \
   --bootstrap-server localhost:19092,localhost:29092,localhost:39092
```
