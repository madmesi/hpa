# hpa
Kubernetes Horizontal Pod Autoscaler with metrics server


## 0) Edit the yaml files in metrics-server/ and then deploy metrics-server
`kubectl create -f metrics-server/`


## 1) Create php-apache deployment 
`cd deploy`

`kubectl create -f php-apache-dep.yaml`

`kubectl create -f php-apache-svc.yaml`


## 2) Create hpa
`kubectl create -f php-apache-hpa.yaml`


## Create Load
`kubectl run -i --tty load-generator --image=busybox /bin/sh`

## inside prompt:
`while true; do wget -q -O- http://php-apache.default.svc.cluster.local; done`


## Check the hpa
`NAME         REFERENCE               TARGETS   MINPODS   MAXPODS   REPLICAS   AGE`

`php-apache   Deployment/php-apache   62%/50%   1         10        10         54m`

## Result
`kubectl get pods`
