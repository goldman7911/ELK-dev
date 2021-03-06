# Estudo ELK

Seguindo:
https://www.elastic.co/guide/en/elastic-stack/current/installing-elastic-stack.html

Feito para uso do WSL2 e Docker Desktop.  
Muito das configurações foram feitas devido a limitações dessa escolha -- principalmente a parte dos bind mounting.

## PRÉ REQUISITOS

 1. Windows 10
 2. WSL2
 3. Docker Desktop
 4. Modificar vm.max_map_count

#### Modificar vm.max_map_count

	wsl -d docker-desktop
	(dentro do container) sysctl -w vm.max_map_count=262144
	(dentro do container) exit

Exemplo:

	PS C:\Users\janki> wsl -d docker-desktop
	DESKTOP-R0FVBGL:/tmp/docker-desktop-root/mnt/host/c/Users/janki# sysctl -w vm.max_map_count=262144
	vm.max_map_count = 262144
	DESKTOP-R0FVBGL:/tmp/docker-desktop-root/mnt/host/c/Users/janki# exit

## Subir o ELK compose

	docker-compose up

## Stop

	docker-compose down -v --remove-orphans

## Limpeza geral do sistema

	docker system prune --all --volumes --force

## Testando

 - elasticsearch

Abra outra aba e envie os comandos:

	curl -X GET "localhost:9200/_cat/nodes?v=true&pretty"
	curl -X GET "localhost:9200/_cat/indices"

 - logstash

Em outra aba execute para acompanhar:

	docker logs logstash --follow --details --timestamps
  
Conecte no container:

	docker exec -u 0 -it logstash bash

Crie ou envie um arquivo para

> ./compose-stack/log-bind/

Resultado esperado: os inputs serão enviados para o elasticsearch.

## port forwarding maquina local

ssh \
-L localhost:5601:172.20.145.230:5601 \
-i oss.pem \
oss@172.20.145.230