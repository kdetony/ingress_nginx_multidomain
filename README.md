# Nginx como ingress controller con Kubernetes
Instalacion de Nginx como Ingress Controller en Kubernetes para 2 dominios.

Instalamos k0s
===

> curl -sSLf https://get.k0s.sh |  sh

> k0s install controller --single

> k0s start

> k0s status

Instalando kubectl
===

> curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"

> chmod +x kubectl && mv kubectl /usr/local/bin/


Configurando acceso al cluster
=====

> mkdir -p /root/.kube

> cp -r /var/lib/k0s/pki/admin.conf /root/.kube/config

Configurando Ingress Controller Nginx
====

> clonamos el repositorio:

git clone https://github.com/kubernetes/ingress-nginx.git

> Agregamos al archivo deploy.yml  **externalIPs** debajo de **NodePort**


**path: ./ingress-nginx/deploy/static/provider/baremetal/deploy.yml**

> externalIPS:
> - IP_PUBLICA

> Deployamos:

kubectl apply -f deploy.yml


Configurando deployments para aplicaciones 
===

ejecutar en el orden de los archivos que se encuentran en los directorios: **kakaroto y me**
