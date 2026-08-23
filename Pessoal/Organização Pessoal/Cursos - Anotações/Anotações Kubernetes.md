---

---
**Master** - Gernecia o cluster, mantém e atualiza o estado, recebe novos comandos

[https://kubernetes.io/pt-br/docs/concepts/overview/components/](https://kubernetes.io/pt-br/docs/concepts/overview/components/)

- API - Conversa entre todos os componentes. Recebe os comandos. **kubectl**
- c-m
- **sched: **componente da camada de gerenciamento que observa os pods recém-criados sem nenhum nó atribuído, e seleciona um nó para executá-los.
- **Etcd: **função de **armazenamento **do tipo Chave-Valor consistente e em alta-disponibilidade usado como repositório de apoio do Kubernetes para todos os dados do cluster.

**Node** - Executa as aplicações (pods)

- **Kubelet**: um serviço executado nos nós que lê os manifestos do container e 
garante que os containers definidos foram iniciados e estão em execução.
 kubectl: a ferramenta de configuração da linha de comando do Kubernetes.
- k-proxy - Comunicação entre os pods

> [!tip] 💡
> **pod** - Pode encapsular um ou mais containeres
Possue um endereço IP

```bash
# Iniciando o minikube
minikube start

# Informações detalhadas dos pods
kubectl get pods -o wide

# Acessar o pod
kubectl exec <nome do pod> -it -- bash
kubectl exec <nome do pod> -it --container <nome do container, caso exista mais de um> -- bash

# Criar um recurso (pod, svc, configmap, replicaset, deployment)
kubectl apply -f <nome do arquivo yaml>

# Deletar um recurso
kubectl delete <pod|svc|configmap|rs|deploy> <nome do recurso>
kubectl delete -f <nome do arquivo yaml>

# Consultar services
kubectl get svc
```

> [!tip] 💡
> Dentro de um cluster Kubernetes, os pods conseguem comunicar-se entre si via endereçamento IP. No entanto, estes IP’s não são fixos/estáveis. Caso um **pod** falhe ele será substituído por outra instância que poderá ter um IP diferente.

Para que a comunicação flua de modo estável, é necessário trabalhar com Services, do tipo **ClusterIP**.

O ClusterIP será um IP estável que sempre vai direcionar para o pod desejado. O link entre eles é feito pelos **Labels**

```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-2
spec:
  type: ClusterIP
  selector:
    app: segundo-pod
  ports:
    - port: 8080
      targetPort: 80
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-2
  labels:
    app: segundo-pod
spec:
  containers:
    - name: container-pod-2
      image: nginx:latest
      ports:
        - containerPort: 80
```

> [!tip] 💡
> Existe um outro tipo de SVC chamado **NodePort**. Na prática, ele funciona exatamente igual ao **ClusterIP**, porém também permite a comunicação de fora do cluster para dentro de um pod

```yaml
apiVersion: v1
kind: Service
metadata:
  name: svc-pod-1
spec:
  type: NodePort
  ports:
    - port: 80
      #targetPort: 80
      nodePort: 30000
  selector:
    app: primeiro-pod
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      env:
        - name: "MYSQL_ROOT_PASSWORD"
          value: "q1w2e3r4"
        - name: "MYSQL_DATABASE"
          value: "empresa"
        - name: "MYSQL_PASSWORD"
          value: "q1w2e3r4"
```

> [!tip] 💡
> Para desacoplar (separar as definições de pod das configurações da aplicação), utilizamos **configMaps.
**Um configMap pode ser utilizado por vários containeres.

```yaml
apiVersion: v1
kind: ConfigMap
metadata:
  name: db-configmap
data:
  MYSQL_ROOT_PASSWORD: q1w2e3r4
  MYSQL_DATABASE: empresa
  MYSQL_PASSWORD: q1w2e3r4
```

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: db-noticias
  labels:
    app: db-noticias
spec:
  containers:
    - name: db-noticias-container
      image: aluracursos/mysql-db:1
      ports:
        - containerPort: 3306
      envFrom:
        - configMapRef:
            name: db-configmap
```

> [!tip] 💡
> **Replica Set **Estrutura do kubernetes que tem a capacidade de encapsular um ou mais pods. Ele controla a quantidade de pods desejados e, caso um falhe, sobre outro automaticamente.
Também atua como **balanceador de carga**

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  name: portal-noticias-replicaset
spec:
  template:
    metadata:
      name: portal-noticias
      labels:
        app: portal-noticias
    spec:
      containers:
        - name: portal-noticias-container
          image: aluracursos/portal-noticias:1
          ports:
            - containerPort: 80
          envFrom:
            - configMapRef:
                name: portal-configmap
  replicas: 3
  selector:
    matchLabels:
      app: portal-noticias
```

> [!tip] 💡
> **Deployment **funcionam exatamente como os ReplicaSet, porém são uma camada acima. Eles provêm a capacidade de controle de versões ao replicaset.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  template:
    metadata:
      name: nginx-pod
      labels:
        app: nginx-pod
    spec:
      containers:
        - name: nginx-container
          image: nginx:latest
          ports:
            - containerPort: 80
  selector:
    matchLabels:
      app: nginx-pod
```

```bash
# Aplicando uma alteração em deployment
kubectl apply -f .\nginx-deployment.yaml --record

# Listando histórico de versões
kubectl rollout history deployment nginx-deployment

# Definindo a anotação da alteração
	kubectl annotate deployment nginx-deployment kubernetes.io/change-cause="Definindo a imagem como latest"

# Fazendo um rollBack
kubectl rollout undo deployment nginx-deployment --to-revision=2
```

> [!tip] 💡
> **pods** são efêmeros, ou seja, não persistem dados por si só.
No kubernetes, a persistência de dados se dá por meio dos seguintes recursos:
**volumes
persistent volumes
persistent volume claim
storage classes
**
**volumes: **Permitem o compartilhamento de arquivos entre contêineres de um mesmo pod. Seu ciclo de vida é independente dos contêineres, mas é dependente do pod


```yaml
apiVersion: v1
kind: Pod
metadata:
  name: pod-volume
spec:
  containers:
    - name: nginx-container
      image: nginx:latest
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: segundo-volume
    - name: jenkins-container
      image: jenkins/jenkins:alpine
      volumeMounts:
        - mountPath: /volume-dentro-do-container
          name: segundo-volume
  volumes:
    - name: segundo-volume
      hostPath:
        path: /home/docker/segundo-volume
        type: DirectoryOrCreate
```

> [!tip] 💡
> **StatefulSets** funciona como Deployments, porém engloba também os PersistentVolumes

```yaml
apiVersion: apps/v1
kind: StatefulSet
metadata:
  name: sistema-noticias-statefulset
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: sistema-noticias
      name: sistema-noticias
    spec:
      containers:
        - name: sistema-noticias-container
          image: aluracursos/sistema-noticias:1
          ports:
            - containerPort: 80
          envFrom:
            - configMapRef:
                name: sistema-configmap
  selector:
    matchLabels:
      app: sistema-noticias
  serviceName: svc-sistema-noticias
```

> [!tip] 💡
> **Probes** são capazes de determinar a saúde do pod baseado no comportamento da aplicação. São configurados dentro do Spec do Pod. Pode ser utilizado em Deployment e StatefulSet também

**livenessProbe: **Sinaliza p/ o kubernetes quando a aplicação não está mais saudável, desencadeando a exclusão do pod e criação de um novo

**readinessProbe: **Sinaliza p/ o kubernetes quando que um pod está pronto a receber novas requisições através de um load balancer ou service.

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: portal-noticias-deployment
spec:
  template:
    metadata:
      name: portal-noticias
      labels:
        app: portal-noticias
    spec:
      containers:
        - name: portal-noticias-container
          image: aluracursos/portal-noticias:1
          ports:
            - containerPort: 80
					envFrom:
						- configMapRef:
								name: portal-configmap
					livenessProbe:
						httpGet:
							path: /
							port: 80
						periodSeconds: 10
						failureThreshold: 3
						initialDelaySeconds: 20
					readinessProbe:
						httpGet:
							path: /
							port: 80
						periodSeconds: 10
						failureThreshold: 3
						initialDelaySeconds: 20
	replicas: 3
  selector:
    matchLabels:
      app: nginx-pod
```

> [!tip] 💡
> **HorizontalPodAutoscaller**

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: portal-noticias-deployment
spec:
  template:
    metadata:
      name: portal-noticias
      labels:
        app: portal-noticias
    spec:
      containers:
        - name: portal-noticias-container
          image: aluracursos/portal-noticias:1
          ports:
            - containerPort: 80
					envFrom:
						- configMapRef:
								name: portal-configmap
					livenessProbe:
						httpGet:
							path: /
							port: 80
						periodSeconds: 10
						failureThreshold: 3
						initialDelaySeconds: 20
					readinessProbe:
						httpGet:
							path: /
							port: 80
						periodSeconds: 10
						failureThreshold: 3
						initialDelaySeconds: 20
					resources:
						requests:
							cpu: 10m
	replicas: 3
  selector:
    matchLabels:
      app: nginx-pod
```

```yaml
apiVersion: autoscaling/v2beta2
kind: HorizontalPodAutoscaler
metadata:
	name: portal-noticias-hpa
spec:
	scaleTargetRef:
		apiVersion: apps/v1
		kind: Deployment
		name: portal-noticias-deployment
	minReplicas: 1
	maxReplicas: 10
	metrics:
		- type: Resource
			resource:
				name: cpu
				target:
					type: Utilization
					averageUtilization: 50
```

> [!tip] 💡
> Para que o kubernetes tenha acesso às métricas do servidor, é necessário configurar um servidor de métricas. O repositório é:
https://github.com/kubernetes-sigs/metrics-server/

No caso do minikube, ele possui addons capazes de fornecer um servidor de métricas

![[SubPages/Pessoal/images/Untitled 129.png]]

![[SubPages/Pessoal/images/Untitled 130.png|Arquitetura de um kluster sem HELM]]

![[SubPages/Pessoal/images/Untitled 131.png]]
