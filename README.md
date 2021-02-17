# Estudo ELK

Seguindo:
https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html

Feito para uso do WSL2 e Docker Desktop. Muito das configurações foram feitas devido a limitações dessa escolha.

## Subir o Kibana junto do compose

configurar o kibana.yml

## Subir o Elasticsearch

docker-compose up --detach es01 es02 es03 kibana  && \
docker-compose run --rm logstash

### Stop

docker-compose down -v --remove-orphans

### Testando

Abra outra aba e envie o comando: 
curl -X GET "localhost:9200/_cat/nodes?v=true&pretty"

Para testar o logstash deve-se digitar no console.