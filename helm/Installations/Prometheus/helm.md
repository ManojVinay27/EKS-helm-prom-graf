Install using helm:
-------------------

Add helm repo:
--------------
    helm repo add prometheus-community https://prometheus-community.github.io/helm-charts

Update helm repo:
-----------------
    helm repo update

Install prometheus:
------------------
    helm install prometheus prometheus-community/prometheus

Expose Prometheus Service:
-------------------------
    kubectl expose service prometheus-server --type=NodePort --target-port=9090 --name=prometheus-server-sample
  
