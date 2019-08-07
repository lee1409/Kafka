# Kafka Docker Example

This is an successful example of create a kafka broker with a zookeeper. It consists of services like Schema Registry, Zookeeper, mysql-connect 

## Usage
Development Usage

    docker-compose -f docker-compose.yml -f docker-compose.dev.yml up -d

Production Usage (Required to modify the volume stored)

    docker-compose -f docker-compose.yml -f docker-compose.dev.yml-f docker-compose.prod.yml up -d

## Logs

There are some error while trying to setup with NAMED_LISTENER_PORT because schema registry cannot recognize. Check Issue [#648](https://github.com/confluentinc/schema-registry/issues/648)

This kafka connect uses Avro Schema to serialize and deseralize the data.

For kafka connect, the INTERNAL_KEY_CONVERTER and INTERNAL_VALUE_CONVERTER is depreciated. Reset it to default (Json) 

