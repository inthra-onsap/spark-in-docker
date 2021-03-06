# Spark standalone mode in docker containers

## Specification
> SPARK_VERSION=2.4.6<br/>
> HADOOP_VERSION=2.7<br/>
> SCALA_VERSION=2.12.4

## Required empty folders in host machine
> /spark/spark-apps # host machine application files will mount to /opt/spark-apps in docker container<br/>
> /spark/spark-data # host machine processing files will mount to /opt/spark-data in docker container

## Linux/Mac
1) Build images

> $> ./build-images.sh

2) Start Spark-master and Spark-workers by docker-compose.yml

> $> docker-compose up

## Submit app to Spark cluster
> $> docker exec -it spark-master /spark/bin/spark-submit --class {ClassName} --master spark://spark-master:7077 /opt/spark-apps/{executable}.jar

## WebUI
> Spark Master: http://localhost:8080 <br/>
> Spark Workers: http://localhost:808[1-3]

## Contact
inthra.onsap@gmail.com
