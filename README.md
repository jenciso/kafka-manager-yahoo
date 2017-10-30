# kafka manager Dockerfile

[kafka manager](https://github.com/yahoo/kafka-manager) is a tool from Yahoo Inc. for managing [Apache Kafka](http://kafka.apache.org).

## Base Docker Image ##

* [centos:7](https://hub.docker.com/_/centos/)

## Howto

### Quick Start

```sh
docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="your-zk.domain:2181" -e APPLICATION_SECRET=letmein jenciso/kafka-manager-yahoo
```

(if you don't define ZK_HOSTS, default value has been set to "localhost:2181")


### Use your own configuration file

You can specify a configuration file via an environment variable.

```sh
docker run [...] -v /path/to/confdir:/opt -e KM_CONFIG=/opt/my_shiny.conf jenciso/kafka-manager-yahoo
```

### Pass arguments to kafka-manager

You can use env variable `KM_ARGS`.

```sh
docker run -it --rm  -p 9000:9000 -e ZK_HOSTS="your-zk.domain:2181" -e APPLICATION_SECRET=letmein -e KM_ARGS=-Djava.net.preferIPv4Stack=true jenciso/kafka-manager-yahoo
```

### Specify a revision

If you want to upgrade/downgrade this Dockerfile, edit it and set `KM_VERSION` and `KM_REVISION` to fetch the release from github.

