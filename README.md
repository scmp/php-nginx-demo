# PHP FPM Benchmark Tools

### Quick Start

To quickly deploy all the things, use the following command: 

```
kubectl apply \
  --filename https://raw.githubusercontent.com/scmp/php-nginx-demo/master/k8s/all.yaml
```

This will bring up all components in there including the namespace `monitoring` for monitoring tools.


If you already have prometheus and grafana in the cluster, , use the following command:

```
kubectl apply \
  --filename https://raw.githubusercontent.com/scmp/php-nginx-demo/master/k8s/without-monitoring.yaml
```

This will only bring up php-fpm benchmark components without monitoring tools.

To remove all components, use the following commands:

```
kubectl delete \
  --filename https://raw.githubusercontent.com/scmp/php-nginx-demo/master/k8s/all.yaml

#or

kubectl apply \
  --filename https://raw.githubusercontent.com/scmp/php-nginx-demo/master/k8s/without-monitoring.yaml
```

### Setup Grafana

- Configure data source for Grafana  
  `Configuration / Data Sources / Add data source`

  - Name: prometheus
  - Type: Prometheus
  - Url: http://prometheus:9090


- Import the dashboard using id `10757`   
  `Dashboards / Manage / Import`

  Reference: https://grafana.com/grafana/dashboards/10757

- To access grafana you can use port forward functionality

  ```
  kubectl port-forward --namespace monitoring service/grafana 3000:3000
  ```