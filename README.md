# Estudo ELK

Seguindo:
https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html

Feito para uso do WSL2 e Docker Desktop. Muito das configurações foram feitas devido a limitações dessa escolha.

## Subir o Elasticsearch

docker-compose up --detach es01 es02 es03 kibana  && \
docker-compose run --rm logstash

### Stop

docker-compose down -v --remove-orphans

### Testando

Abra outra aba e envie o comando: 
curl -X GET "localhost:9200/_cat/nodes?v=true&pretty"

Para testar o logstash deve-se digitar no console.
exemplo:
    {"name": "Jankiel"}

output:
{
          "host" => "f49045bca097",
      "@version" => "1",
       "message" => "{\"name\": \"Jankiel\"}",
    "@timestamp" => 2021-02-17T21:34:24.204Z
}