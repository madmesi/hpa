# hpa
Kubernetes Horizontal Pod Autoscaler with metrics server

## 0) deploy metrics-server
kubectl create -f metrics-server


## Create Load
kubectl run -i --tty load-generator --image=busybox /bin/sh

## inside prompt:
while true; do wget -q -O- http://php-apache.default.svc.cluster.local; done
