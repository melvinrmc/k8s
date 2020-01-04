# k8s
Archivos importantes para ejecutar los ejemplos de [connect-applications](https://kubernetes.io/docs/concepts/services-networking/connect-applications-service/)

## curlpod.yaml
Contiene un curl-deployment que luego de levantado puede invocarse y luego hacer curl utilizando el dns de cualquier servicio de kubernetes de la siguiente manera
```
kubectl apply -f ./curlpod.yaml
kubectl exec curl-deployment-1515033274-1410r -- curl https://my-nginx --cacert /etc/nginx/ssl/tls.crt
```
Como alternativa se tiene
`kubectl run curl --image=radial/busyboxplus:curl -i --tty`
que levanta un contenedor y da acceso a linea de comando para ejecutar curl utilizando el dns kubernetes para los servicios

## ingress-rules-v2.yaml
Versión mejorada de webapp-ingress que incluye seguridad TLS utilizando Secrets

Adding TLS to Katacoda Example
Katacoda Example with TLS
https://katacoda.com/courses/kubernetes/create-kubernetes-ingress-routes

## nginx-secure-app.yaml
Servicio my-nginx con seguridad

## pod-nginx.yaml
Pod nginx básico para experimentar

## redis-cache y web-server
con pod affinity para desplegar estrictamente el par [redis-cache, web-server] por nodo

## redis-cache-preferred.yaml y web-server-preferred.yaml
Con preferred affinity para desplegar preferentemente el par [redis-cache, web-server] por nodo

## run-my-nginx.yaml
Deployment nginx básico para experimentar

## pod-nginx-with-env-secrets.yaml
Simple pod nginx con variables de entorno utilizando secrets

create secret before:

`kubectl create secret generic mysecret --from-literal=username=admin --from-literal=password=secret --from-literal=endpoint1=http://localhost:8080`
