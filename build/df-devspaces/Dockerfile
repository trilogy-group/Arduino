FROM openjdk:8

RUN apt-get update && \
    apt-get install -y git make gcc ant unzip openjfx && \
    apt-get clean all

WORKDIR /data
