FROM listerine/dev-env
MAINTAINER Jon Ferretti

RUN apt-get update && apt-get install -y default-jre default-jdk && apt-get install -y openjdk-7-jre openjdk-7-jdk unzip
RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.4.zip
RUN unzip elasticsearch-1.4.4.zip
RUN elasticsearch-1.4.4/bin/plugin -i elasticsearch/marvel/latest
RUN git clone https://github.com/LISTERINE/elasticsearch-tutorial.git

WORKDIR elasticsearch-tutorial
