helm install elasticsearch bitnami/elasticsearch -f elasticsearch-values.yaml -n logging
helm install logstash bitnami/logstash -f logstash-values.yaml -n logging
helm install filebeat elastic/filebeat -f filebeat-values.yaml -n logging
helm install kibana bitnami/kibana -f kibana-values.yaml -n logging
