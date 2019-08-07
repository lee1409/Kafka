
# Kafka Docker Example

  

This is an successful example of create a kafka broker with a zookeeper. It consists of services like Schema Registry, Zookeeper, kafka-connect, cp-ksql-server. 

#Noted: The MySQL jar file is already included in the repository. 

  

## Installation

Development

    docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d

Production Usage (Required to modify the volume stored)

    docker-compose -f docker-compose.yml -f docker-compose.dev.yml-f docker-compose.prod.yml up -d

  
## Usage

The purpose to setup is primarily used for KSQL only. Before using Kafka, you need to send data into Kafka using kafka-connect. 

To use KSQL, simple download KSQL CLI and run the script

    $ <path-to-confluent>/bin/ksql <ksql-server-URL>

## Logs
There are some error while trying to setup with NAMED_LISTENER_PORT because schema registry cannot recognize. Therefore, the kafka broker is **not** exposed to host port. Check Issue [#648](https://github.com/confluentinc/schema-registry/issues/648)

This kafka connect uses Avro Schema to serialize and deseralize the data.

For kafka connect, the INTERNAL_KEY_CONVERTER and INTERNAL_VALUE_CONVERTER is depreciated. Reset it to default (Json)

