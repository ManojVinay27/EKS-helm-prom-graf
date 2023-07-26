Install using helm:
------------------

Add helm repo:
-------------
    helm repo add grafana https://grafana.github.io/helm-charts

Update helm repo:
----------------
    helm repo update
  
Install Grafana:
----------------
    helm install grafana grafana/grafana

Expose grafana service:
-----------------------
    kubectl expose service grafana --type=NodePort --target-port=3000 --name=grafana-sample
