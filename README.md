----*-----
kubectl create -f nginx-deployment.yaml ---> For creating application for log generation. The container outputs access logs to stdout/stderr, which are picked up by Filebeat.
helm install elasticsearch bitnami/elasticsearch -f elasticsearch-values.yaml -n logging  ---> It stores all logs and provides powerful search capabilities( Main backup want to enabled)
helm install logstash bitnami/logstash -f logstash-values.yaml -n logging ---->Logstash is responsible for ingesting, transforming, and routing logs. In this setup, it receives logs from Filebeat and forwards them to Elasticsearch.
helm install filebeat elastic/filebeat -f filebeat-values.yaml -n logging -----> It's runs as a DaemonSet on all nodes and collects container logs from /var/log/containers/*.log. It forwards these logs to Logstash on port 5044
helm install kibana bitnami/kibana -f kibana-values.yaml -n logging ----->It provides a graphical interface to explore, visualize, and search logs stored in Elasticsearch.
