# Estudo ELK

Seguindo:
https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html

## Subir o Kibana junto do compose

configurar o kibana.yml

## Subir o Elasticsearch

docker-compose up 

### Testando

Abra outra aba e envie o comando: 
curl -X GET "localhost:9200/_cat/nodes?v=true&pretty"

Para testar o logstash deve-se digitar no console.

### Stopar

docker-compose down -v --remove-orphans