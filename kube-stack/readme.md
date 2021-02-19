# Instalar

helm install elasticsearch elastic/elasticsearch
helm install --values elasticsearch-dev-values.yml --name-template elasticsearch-indra elastic/elasticsearch
helm install --values kibana-dev-values.yml --name-template indra elastic/kibana
helm install --values logstash-dev-values.yml --name-template indra elastic/logstash

helm install --debug -v 6 --values logstash-dev-values.yml logstash elastic/logstash

# Forward da porta
kubectl port-forward elastic-indra-master-0 9200:9200 &



helm install --debug -v 6 --values elasticsearch-dev-values.yml elasticsearch elastic/elasticsearch
helm install --debug -v 6 --values kibana-dev-values.yml kibana elastic/kibana
helm install --debug -v 6 --values logstash-dev-values.yml logstash elastic/logstash