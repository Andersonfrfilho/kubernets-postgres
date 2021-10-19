1 - criar cluster com o kind:
```bash 
kind create cluster
```
2 - informações sobre o cluster pelo o kubectl
```bash
kubectl cluster-info --context kind-kind
```

2.1 - listar configurações de clusters
```bash
kubectl config get-clusters
```
2.2 - mudar contexto de cluster
```bash
kubectl config use-context nome-do-cluster
```

3 - create a cluster with config and name
```bash
kind create cluster --config=k8s/kind.yaml --name=fullcycle
```
1 - mount image:
```docker build -t andersonfrfilho/hello-nodejs .```
2 - test image
```docker run --rm -p 3000:3000 andersonfrfilho/hello-nodejs```

3 - criar pod
```sh
kubectl apply -f k8s/pod.yaml
```

4 - Olhar os logs
kubectl logs nomeDoPod

5 - Deletar deployment
kubectl delete deploy nodeDeployment

5.1 - Deletar um statefulset
kubectl delete StatefulSet postgres

## para acessar os pods vc temq eu ter um mecanismo de rede que são os services

7 - caso tenhaproblema no get de pods executar:
```sh
kubectl config set-context --current --namespace=default
```

8 - Executar comando dentro dos pods:
``` kubectl exec -it nodejs-server-name -- bash```

9 - verificar service criado (postgres-h) nome_service:
```ping postgres-h```

10 - verificar service por pod (postgres-0.postgres-h) nome do nome_pod.nome_service
```ping postgres-0.postgres-h```
obs:
- ```pod.service.namespace.service.cluster.local```
- ```postgres-3.postgres-h.default.svc.cluster.local```