# wordpress-docker-k8s
Wordpress on Docker and deploy to Kubernetes

## Install and deploy to k8s
### Helm install
```sh
helm install my-release oci://registry-1.docker.io/bitnamicharts/wordpress 
```
### Get IP for access
```sh
kubectl get svc --namespace default my-release-wordpress --template "{{ range (index .status.loadBalancer.ingress 0) }}{{.}}{{ end }}"
```
### Get Password 
```sh
kubectl get secret --namespace default my-release-wordpress -o jsonpath="{.data.wordpress-password}" | base64 --decode
```