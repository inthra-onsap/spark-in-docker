# Spark standalone mode in docker containers


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

