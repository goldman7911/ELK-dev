FROM docker.elastic.co/logstash/logstash:7.11.1
RUN rm -f /usr/share/logstash/pipeline/logstash.conf 
RUN mkdir /usr/share/logstash/arquivos-entrada
ADD config/ /usr/share/logstash/config/
ADD pipeline/ /usr/share/logstash/pipeline/
ENV MONITORING_ELASTICSEARCH_HOSTS="http://elastic:9200"