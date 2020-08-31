# Spark standalone mode in docker containers

## Specification
> SPARK_VERSION=2.4.6<br/>
> HADOOP_VERSION=2.7<br/>
> SCALA_VERSION=2.12.4

## Required empty folders in host machine
> /spark/spark-apps # application files<br/>
> /spark/spark-data # processing files

## Linux/Mac
1) Build images

> $> ./build-images.sh

2) Start Spark-master and Spark-workers by docker-compose.yml

> $> docker-compose up

## Websites
> Spark Master: http://localhost:8080 <br/>
> Spark Workers: http://localhost:808[1-3]

