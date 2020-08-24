FROM openjdk:8-jdk-alpine3.7

ENV DAEMON_RUN=true
ENV SPARK_VERSION=2.4.6
ENV HADOOP_VERSION=2.7
ENV SCALA_HOME=/usr/share/scala
ENV SCALA_VERSION=2.12.4

RUN apk add --no-cache --virtual=.build-dependencies wget ca-certificates && \
	apk add --no-cache bash curl jq && \
	cd "/tmp" && \
	wget --no-verbose "https://downloads.typesafe.com/scala/${SCALA_VERSION}/scala-${SCALA_VERSION}.tgz" && \
	tar xzf "scala-${SCALA_VERSION}.tgz" && \
	mkdir "${SCALA_HOME}" && \
	rm "/tmp/scala-${SCALA_VERSION}/bin/"*.bat && \
	mv "/tmp/scala-${SCALA_VERSION}/bin" "/tmp/scala-${SCALA_VERSION}/lib" "${SCALA_HOME}" && \
	ln -s "${SCALA_HOME}/bin/"* "/usr/bin/" && \
	apk del .build-dependencies && \
	rm -rf "/tmp/"*


#Scala installation
RUN apk update && \
	apk add ca-certificates wget tar && \
	mkdir -p "/usr/local/sbt" && \
	wget --max-redirect=10 --no-check-certificate "https://dl.bintray.com/sbt/native-packages/sbt/0.13.15/sbt-0.13.15.tgz" && \
	tar xzf sbt-0.13.15.tgz && \
	mv /sbt/* /usr/local/sbt/ && \
	export PATH="/usr/local/sbt/bin:$PATH" && \
	sbt sbtVersion

RUN apk add --no-cache python3

RUN wget --no-verbose http://apache.mirror.iphh.net/spark/spark-${SPARK_VERSION}/spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && ls -la && \
	tar -xzf spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz && \
	mv spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION} spark && \
	rm spark-${SPARK_VERSION}-bin-hadoop${HADOOP_VERSION}.tgz
