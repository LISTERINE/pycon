FROM listerine/dev-env
MAINTAINER Jon Ferretti

RUN apt-get install -y openjdk-7-jdk unzip
RUN wget https://download.elasticsearch.org/elasticsearch/elasticsearch/elasticsearch-1.4.4.zip
RUN unzip elasticsearch-1.4.4.zip
RUN elasticsearch-1.4.4/bin/plugin -i elasticsearch/marvel/latest
RUN https://github.com/LISTERINE/elasticsearch-tutorial.git
