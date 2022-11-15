# Kubernets - Atividade 2 de Infrastructure &amp; Cloud Computing

## Descrição da atividade:

<i><b>"Subir dois pods, nginx e mysql, mapeando a porta 80 do nginx para acesso externo ao cluster e permitir que o contêiner do nginx tenha comunicação de rede no contêiner mysql pela porta 3306.
A atividade pode ser feita localmente (minikube/Docker Desktop), AKS (Azure), EKS (AWS) ou no GKE (GCP).

Se quiser criar o cluster Kubernetes com Terraform é opcional.
Enviar os arquivos yaml pelo GitHub.
O código enviado deve satisfazer exatamente o que foi pedido no enunciado, caso haja código faltando ou sobrando terá desconto de nota."</b></i>

## Resolução da atividade
1. Criação e exposição externa do *pod* NGINX
```
kubectl run ngpod --image=nginx:latest
kubectl expose pods ngpod --type=NodePort --port=80 --name nginx-expose-service
minikube service nginx-expose-service
```
2. Criação e exposição do *pod*  MySQL
```
kubectl run mysql --image=mysql:latest --env "MYSQL_ROOT_PASSWORD=1234"
kubectl expose pods mysql --type=ClusterIP --port=3306 --name nginx-mysql-network
minikube service nginx-mysql-network
```
