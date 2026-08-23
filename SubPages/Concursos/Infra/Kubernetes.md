---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-04-18T09:37:00
Owner:
  - Eduardo Quinalha
---
[https://traefik.io/glossary/k3s-explained/](https://traefik.io/glossary/k3s-explained/)

> [!note]+ # Mapa Mental
> ![[K8s.png]]

> [!note]+ # Materiais Extras
> ## Material de estudo para DCA
> 
> [https://github.com/DevOps-Academy-Org/dca-prep-guide](https://github.com/DevOps-Academy-Org/dca-prep-guide)
> 
> [https://github.com/Evalle/DCA](https://github.com/Evalle/DCA)
> 
> [https://medium.com/bb-tutorials-and-thoughts/250-practice-questions-for-the-dca-exam-84f3b9e8f5ce](https://medium.com/bb-tutorials-and-thoughts/250-practice-questions-for-the-dca-exam-84f3b9e8f5ce)

# Arquitetura do Cluster Kubernetes

![[Untitled 664.png]]

- **Componentes do Master**
	- Fornecem o **control plane**
	- Podem ser executados em qualquer máquina do cluster, porém é usual que estes componentes executem na mesma máquina.
	- Não recomenda-se que executem pods nesta máquina
	- **kube-apiserver**
		- Valida e configura dados para os objetos da API: pods, services, replica set
		- Suporta REST
		- Cuida da autenticação e autorização para interagir com o cluster
		- Usualmente interagimos com a API via comando `kubectl`
	- **kube-scheduler**
		- Monitora pods recém criados e que não tenham um nó associado, fazendo a designação de um nó para estes
		- Considera regras implícitas e explícitas para a designação
	- **kube-controller-manager**
		- Roda em um loop que constantemente compara o estado atual dos workloads com o que foi especificado
		- Assim que um desvio for identificado, uma ação é tomada, como por exemplo, recriar um pod
		- Tipos
			- Node Lifecycle controller
			- DaemonSet controller
			- Deployment controller
			- Namespace controller
	- **etcd**
		- **Somente o kube-apiserver comunica-se diretamente com o etcd!**
		- Qualquer interação com o etcd é feita por meio do API Server
		- Banco de dados chave-valor de alta disponibilidade
		- Armazena configurações, estado e metadados
		- É daqui que o kubernetes monitora o status dos pods também
	- **cloud-controller-manager**
		- Gerencia controllers associados com cloud providers

> [!tip] 💡
> Principais: API Server, Scheduler, Controller Manager, etcd

- **Componentes dos Nós**
	- **Container Runtime**
		- Responsável pela execução dos contêineres
		- Componente independente do kubernetes em si. Por exemplo, docker
		- Kubernetes Suporta vários contêiner runtimes:
			- Docker
			- conteinerd
			- cri-o
			- rktlet
	- **kubelet**
		- Agente que é executado em cada nó do cluster
		- Faz a interface entre o container-runtime e a máquina propriamente dita
		- Garante que os contêineres estejam sendo executados em todos os pods
		- Não gerencia contêineres que não sejam criados pelo kubernetes
	- **kube-proxy**
		- Proxy de rede executado em cada nó do cluster
		- Faz o encaminhamento de conexões
		- Camada de abstração do serviço
> [!tip] 💡
> Principais: Container Runtime, Kubelet, Kube-proxy
- **Addons**
	- Pods e serviços que implementam recursos de cluster
		- DNS
		- Web UI
		- Monitoramento de recursos
		- Log a nível de cluster

![[efj4eq30q56ute916yfi.png]]

## HA Cluster

- Clusters de alta disponibilidade
- A fim de evitar pontos únicos de falha que possam comprometer todo o cluster
- É necessário múltiplos Masters
- Etcd Quorum
	- Em alta disponibilidade, as decisões serão feita por maioria dos votos (caso haja discrepância no etcd)
	- Sendo assim, num cluster de** n **membros, o quórum mínimo será `**n/2 + 1**`
	- Ou seja, serão necessárias pelo menos 3 réplicas do etcd para o funcionamento em HA

# Objetos (Workloads)

- **Pods**
	- Menor unidade dentro do Kubernetes
	- Um pod pode rodar um ou mais contêineres dentro dele
	- Apesar disso, é recomendado que apenas um container rode em um pod
	- Pode conter volumes
	- Cada Pod recebe um endereço IP
	- Este IP varia cada vez que o Pod é terminado e outro assume o lugar
- **Services**
	- Como os pods são transientes, o serviço provido por um ou mais pods deve ser exposto por meio de services
	- Um service tem o objetivo que garantir um IP estável para um serviço, independente o IP do Pod que esteja por baixo
	- O ciclo de vida do service e do pod são desconectados
	- Pode ser um external service
		- Neste caso o IP e porta estarão disponíveis para fora do cluster
	- Permitem que serviços conversem entre si
	- Faz Load Balancer
	- Permitem realizar service discovery
	- Tipos:
		- **ClusterIP**
			- Acessível somente dentro do Cluster
			- Default
			- Faz LoadBalance
		- **NodePort**
			- Exposto para fora do Cluster
			- Faz com que uma porta fixa seja disponibilizada em cada worker node para comunicação com o serviço especificado
			- Não passa pelo ingress
			- Permite o acesso direto ao worker node (não é muito seguro)
			- Configurado pela especificação `nodePort: <porta>`
			- Possui um range específico: **30000 a 32767**
		- **LoadBalancer**
			- Permite o uso de um serviço específico de LoadBalancer externo
			- É uma extensão do NodePort, que por sua vez, é uma extensão de ClusterIP
			- Cada plataforma utilizará sua própria solução
			- Também especifica uma nodePort em cada worker, porém esta estará acessível apenas para o IP do LoadBalancer
		- **Headless**
			- Comunicação diretamente com o Pod
			- Utilizado em statefulsets para replicação entre os Pods
			- Permite realizar uma busca DNS que retornará o IP do Pod diretamente
			- Definido com a especificação `clusterIP: None`
![[Untitled 665.png]]
- **Ingess**
	- Um service pode externalizar um IP e porta para acesso ao pod para fora do cluster kubernetes, no entanto o acesso ainda será efetuado por meio de um IP:Porta
	- O Ingress permite externalizar serviços por meio de uma URL
```yaml
apiVersion: networking.k8s.io/v1beta1
kind: Ingress
metadata:
	name: myapp-ingress
spec:
	# A configuração abaixo habilita HTTPS para o domínio
	# O secret do TLS possui algumas especificidades que estão mais abaixo
	tls:
	- hosts:
		- myapp.com
		secretName: myapp-secret-tls
	# Aqui pode-se especificar múltiplos subdomínios, ou paths para redirecionar as requisições para diferentes serviços
	rules:
	- host: myapp.com
		http:
			paths:
			- path: /analytics
				backend:
					serviceName: analytics-service
					servicePort: 3000
			- path: /shopping
				backend:
					serviceName: shopping-service
					servicePort: 8080
			- backend:
					serviceName: myapp-internal-service
					servicePort: 8080
---
apiVersion: v1
kind: Service
metadata:
	name: myapp-internal-service
spec:
	selector:
		app: myapp
	# Ingress utiliza o type = ClusterIP que é o default
	ports:
		- protocol: TCP
			port: 8080
			targetPort: 8080
			# Como o type utilizado pelo Ingress é ClusterIP, não é necessário especificar nodePort
---
apiVersion: v1
kind: Secret
metadata:
	name: myapp-secret-tls
	# Deve ser utilizado o mesmo namespace do ingress controller
	namespace: default
data:
	tls.crt: base64 encoded cert
	tls.key: base64 encoded key
# Para certificados, deve ser especificado o type do secret
type: kubernetes.io/tls
```
![[Untitled 666.png]]
	- Ingress depende de uma implementação, chamado **Ingress Controller**
		- Corresponde a um pod ou um conjunto deles
![[Untitled 667.png]]
		- Existem vários fornecedores de ingress controller. Por padrão, o kubernetes utiliza o **Nginx**
	- Ingress define um `default-http-backend` e encaminha todas as requisições que não encontrarem uma regra para este serviço
	- Para ter uma página padrão de erro, basta criar um service com o mesmo nome
	- 
- **Volumes**
	- Permite a persistência dos dados entre os pods
	- Funciona como pontos de montagem do linux
	- Tem o mesmo ciclo de vida do pod que o possui
![[Untitled 668.png]]
- **Namespaces**
	- Utilizado para subdividir o cluster e permitir o trabalho de várias equipes
	- Cada recurso pode estar apenas em um namespace
	- Não podem ser aninhados
- **ReplicacaSet**
	- Mantêm um conjunto estável de pods em execução
	- Garantir disponibilidade de pods idênticos
	- Cria e exclui pods conforme necessário a fim de atender as regras definidas
- **Deployment**
> [!note] 🔥
> Enquanto um Service se encarrega de expor o serviço provido pelos pods (replicaset) via rede, o Deployment se encarrega de especificar e gerenciar o conjunto de pods para garantir que estejam funcionando conforme a especificação

Um **deployment** sem **service** não pode ser acessado de fora ou por outros serviços

	- Recurso de alto nível para deploy de aplicações
	- Cria automaticamente um Replica Set
	- Gerencia o Replica Set e garante que a última versão da aplicação esteja rodando no número desejado de Pods
	- Define regras de atualização e rollback dos Pods
	- Permite a injeção de configurações
	- Na prática, não se cria o pod, service nem o replicaset diretamente. O que se faz é criar um deployment que se encarregará de especificar e criar o Pod, expor ele através de um service e mantê-lo operando por um conjunto de réplicas (replicaset)
![[Untitled 669.png]]
![[Untitled 670.png]]
![[Untitled 671.png|Sem deployment]]
![[Untitled 672.png|Com Deployment]]
- **StatefulSet**
	- Semelhante ao deployment, porém específico para aplicações stateful como bases de dados
	- Usado tipicamente por bases de dados
	- Na prática, tanto deployment quanto statefulsets podem usar persistência provida pelo kubernetes
		- Qual a diferença?
			- Quando um pod stateless (deployment) é criado, escalado ou excluído, isso pode ser feito em qualquer ordem
			- Os pods podem ter qualquer identificação ramdomica
			- Uma aplicação stateful, quando escalada horizontalmente, deve ter apenas um nó que pode escrever dados
			- Caso dois nós tenham permissão para escrever simultaneamente, pode ocorrer inconsistência nos dados
			- Sendo assim, o escalamento horizontal de uma aplicação stateful (base de dados, tipicamente), é feito num modelo master/slaves
			- Apenas o nó mestre pode escrever. Os escravos podem ler simultaneamente, sem problemas
			- Cada nó terá seu próprio storage físico, as informações serão sincronizadas entre eles
![[Untitled 673.png]]
			- Em um statefulset, a identificação do pod é mantida quando este é substituído
![[Untitled 674.png]]
![[Untitled 675.png]]
			- As réplicas são criadas em ordem. O novo pod só será criado após confirmação de que o anterior está rodando
			- Cada Pod de um statefulset tem uma entrada de DNS para si (um service)
![[Untitled 676.png]]
			- Cada nó irá manter seu estado anterior e seu nome, mesmo depois de recriado
	- É mais prático manter bases de dados fora do kluster kubertes e apenas aplicações stateless dentro
	- Os pods gerenciados por um deployment são stateless e intercambiáveis. Não possuem um estado persistente
		- Deployments não matém a identificação dos pods. Os nomes são gerados automaticamente.
	- Statefulset garante identidades persistentes para os pods
	- Pods stateful
	- São escalados verticalmente, enquanto que o deployment faz escalabilidade horizontal
![[Untitled 677.png]]
- **DaemonSet**
	- Um equivalente de Deployment, porém visa garantir que um determinado Pod esteja presente em cada um dos Workers ou em um grupo deles especificado
	- Útil para agentes de monitoramento, por exemplo
- **Job**
	- Tipo especial de Pod cujo objetivo é iniciar, executar uma tarefa (comando) e depois encerrar
	- Em Pods normais, quando este terminar, o Kubernetes irá tentar reiniciá-lo. Como a função do Job é executar e sair, o Kubernetes não tentará reiniciá-lo
- **CronJob**
	- Similar ao Job, porém executa de acordo com um agendamento
- **ConfigMap**
	- Permite externalizar configurações de forma que não fiquei hardcoded nas aplicações
	- Utilizam variáveis de ambiente
- **Secret**
	- Um tipo de configmap específico para credenciais
	- Codificado em base64

## Comandos, exemplos:

- `kubectl create deployment nginx-deployment --image=nginx`
	- Inicia um deployment, contendo um pod baseado na imagem especificada
- `kubectl edit deployment nginx-deployment`
	- Edita o deployment especificado (mesmo que não tenha sido criado via arquivo yaml)
- `kubectl apply -f <arquivo.yaml>`
	- Cria o recurso baseado em um arquivo YAML
	- O kubernetes irá detectar automaticamente se trata-se de uma **criação** de um novo recurso ou um **update** de recurso existente
- `kubectl exec -it <Pod name> — bin/bash`
	- Roda um comando no pod
	- Neste caso, dará acesso ao shell do mesmo
- `kubectl logs <Pod name>`

## Exemplos

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: mongo-express-deployment
	# Quando não especificado, os objetos serão criados no namespace default
	namespace: database
  labels:
    app: mongo-express
# Especificações do Deployment e ReplicaSet
spec:
  replicas: 1
  selector:
    matchLabels:
      app: mongo-express
	# Template que será utilizado para criar os conteineres dinamicamente, pelo Kubernetes
  template:
    metadata:
      labels:
        app: mongo-express
		# Especificação do conteiner
    spec:
      containers:
      - name: mongo-express
        image: mongo-express
        ports:
        - containerPort: 8081
        env:
          - name: ME_CONFIG_MONGODB_ADMINUSERNAME
            valueFrom:
              secretKeyRef: 
                name: mongodb-secret
                key: mongo-root-username
          - name: ME_CONFIG_MONGODB_ADMINPASSWORD
            valueFrom:
              secretKeyRef: 
                name: mongodb-secret
                key: mongo-root-password
          - name: ME_CONFIG_MONGODB_SERVER
            valueFrom:
              configMapKeyRef:
                name: mongo-express-configmap
                key: database_url
# Arquivos YAML podem ser concatenados em um único arquivo
---
apiVersion: v1
kind: Service
metadata:
  name: mongo-express-service
spec:
  selector:
    app: mongo-express
  # Quando não especificado, o type será ClusterIP que é um endereço interno. 
  # LoadBalancer fornece um IP externo para acesso à aplicação.
  type: LoadBalancer
  ports:
    - protocol: TCP
      port: 8081
      targetPort: 8081
      # Para o type: LoadBalancer é necessário especificar um nodePort
      # Há um range pré-definido para NodePort: 30000 ~ 32767
      # Para uso no minikube, o external-IP ficará como pendente porquê é necessário atribuir um IP via minikube:
      # minikube service <nome do service>
      nodePort: 30000
```

- Partes que compõem um arquivo de configuração:
	- Tipo do componente
		- apiVersion
			- Cada componente tem uma api específica
		- kind
	- metadata
		- name
		- labels
	- specs
		- configurações do componente
		- Template
			- Pojeto (blueprint) para configurar um pod (o que será feito dinamicamente pelo kubernetes)
	- Labels e Selectors
		- Faz as conexões entre deployments/services com os pods

## Namespaces

- Organizam os recursos
- Por padrão, o kubernetes vem com 4 namespaces definidos
	- **kube-system**
		- Processos do kubectl e controle do master
	- **kube-public**
		- Informações sobre o cluster
	- **kube-node-lease**
	- **default**
		- Utilizado por padão se nenhum outro namespace for criado ou especificado
- Podem ser criados via linha de comando ou arquivos YAML
	- `kubectl create namespace <nome>`
- Objetos como ConfigMap e Secrets não podem ser compartilhados por diferentes namespaces
- Services, podem ser acessados de outros namespaces, por exemplo:
	- `db_url: mysql-service.database`
		- Neste exemplo, database é o nome do namespace ao qual se refere
- Alguns objetos não podem ser confinados em namespaces por serem de natureza global:
	- Volumes
	- Nodes
	- Recursos que não são “namespaced” podem ser listados: `kubectl api-resources —namespaced=false`
- O comando `kubectl get <tipo>` por padrão lista somente objetos do namespace `default`
	- Para visualizar objetos de um namespace específico deve-se utilizar `-n <namespace>`

# HELM

- Package Manager para Kubernetes
- Template Engine
- Armazena arquivos YAML com configurações
- Exemplo:
	- Deseja-se fazer um deploy de uma infrastrutura do Elastic Stack no kubernetes
	- Para isso será necessário:
		- Stateful Set
		- ConfigMap
		- Secret
		- Users e permissões
		- Services
	- Ao invés de fazer tudo manualmente, pode-se procurar por um conjunto de arquivos YAML para tudo isso
	- O conjunto de YAML files padrão para este tipo de configurações é chamado Helm Chart
	- O local onde os Helm Charts ficam armazenados, são chamados Helm Registry

# Volumes

- O ponto de montagem não pode estar atrelado a nenhum dos nós pois deve estar disponível a todos eles
- Requerimentos de Storage
	- Ciclo de vida independente do Pod
	- Disponível para todos os nós
	- Deve ser resiliente mesmo que o cluster falhe

## Persistent Volume - PV

- Não são “namespaced”
- Podem ser remotos ou locais
- Recurso disponível para o cluster
- Criado via arquivo YAML
- É uma entidade lógica que irá fazer uma interface para o armazenamento físico
	- Diso local
	- Servidor NFS

## Persistent Volume Claim - PVC

- Também criado via YAML files
- PVC pode ser namespaced e deve estar no mesmo namespace do Pod
- É referenciado pelo YAML do pod
- O Pod solicita uma unidade de storage via PVC
- O Cluster irá determinar, dentre os PV que possui, um que atenda à solicitação e disponibilizar para o Pod

![[Untitled 678.png]]

## Storage Class

- Cria os PV’s dinamicamente

# Hooks

No Kubernetes, hooks são pontos de integração que permitem **executar scripts ou ações específicas** em momentos definidos do ciclo de vida de um contêiner ou pod. Existem dois tipos principais de hooks no Kubernetes:

1. **Lifecycle Hooks**: São usados para executar ações específicas durante os estágios de inicialização e encerramento dos contêineres em um pod.
	- **PostStart Hook**: É executado imediatamente após o contêiner ser criado. Pode ser usado para realizar ações de inicialização adicionais que não são possíveis dentro da imagem do contêiner.
	- **PreStop Hook**: É executado antes do contêiner ser encerrado. Pode ser usado para executar ações de limpeza, como a finalização de conexões ou a gravação de logs.
2. **Admission Hooks**: São usados para modificar ou validar as solicitações ao servidor da API do Kubernetes antes que os objetos sejam persistidos no etcd (a base de dados do Kubernetes). Existem dois tipos principais de admission hooks:
	- **Mutating Admission Webhooks**: Podem modificar os objetos antes que eles sejam persistidos.
	- **Validating Admission Webhooks**: Podem validar os objetos e rejeitar solicitações se não atenderem a certos critérios.

### Exemplos de Uso

3. **PostStart Hook:**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: lifecycle-demo
spec:
  containers:
  - name: lifecycle-demo-container
    image: busybox
    lifecycle:
      postStart:
        exec:
          command: ["/bin/sh", "-c", "echo Hello from the PostStart handler > /usr/share/message"]

```
4. **PreStop Hook:**
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: lifecycle-demo
spec:
  containers:
  - name: lifecycle-demo-container
    image: busybox
    lifecycle:
      preStop:
        exec:
          command: ["/bin/sh", "-c", "echo Goodbye from the PreStop handler > /usr/share/message"]

```
5. **Admission Webhook:**
Para configurar um webhook de admissão, você geralmente cria um serviço que responde a eventos do Kubernetes e o configura usando um objeto `MutatingWebhookConfiguration` ou `ValidatingWebhookConfiguration`. Aqui está um exemplo básico:
```yaml
apiVersion: admissionregistration.k8s.io/v1
kind: ValidatingWebhookConfiguration
metadata:
  name: example-webhook
webhooks:
- name: validate.example.com
  clientConfig:
    service:
      name: example-service
      namespace: example-namespace
      path: "/validate"
    caBundle: <ca-bundle>
  rules:
  - operations: ["CREATE", "UPDATE"]
    apiGroups: [""]
    apiVersions: ["v1"]
    resources: ["pods"]

```

Os hooks permitem maior controle sobre o comportamento dos contêineres e pods, proporcionando flexibilidade e capacidade de customização para diversas necessidades operacionais.

# K3s vs K8s

## K3s

- Distribuição leve de kubernetes, criada pela Rancher Labs
- Certificada pela Cloud Native Computing Foundation (CNCF)
	- Isto significa que uma aplicação que rode em outra distribuição Kubernetes certificada, também vai rodar no K3s
- Roda por apenas um binário e que é bem pequeno (Cerca de 15MB)
- Requer poucos recursos computacionais
- Roda com uma base de dados SQLite, ao invés do etcd
- Utiliza o Traefik Proxy como ingress controller
- Fora isso, não muda nenhuma funcionalidade “core” do Kubernetes
- **Não é um fork do Kubernetes**
- É bastante indicado para uso com IoT, sistemas embarcados, satelites e outras aplicações “Edge”
- Pode rodar como Single Node

![[Untitled 679.png]]
