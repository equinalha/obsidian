---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:40:00
Owner:
  - Eduardo Quinalha
---
[https://www.youtube.com/watch?v=Zn6ujbEKlaQ](https://www.youtube.com/watch?v=Zn6ujbEKlaQ)

[https://www.rancher.academy/courses/take/rancher-basics/lessons/42677287-introduction-lesson](https://www.rancher.academy/courses/take/rancher-basics/lessons/42677287-introduction-lesson)

> [!tip] 💡
> **RKE2 **Trabalha com o **containerd **como default container runtime

# Características

- Visa facilitar a administração de clusters kubernetes
- Funciona com qualquer distribuição de kubernetes:
	- k3s
	- RKE → Rancher
	- minikube
	- EKS → Amazon
- Fornece tanto GUI como CLI
- Pode administrar vários clusters simultaneamente
- Incluindo clusters na nuvem
- **Para melhor performance e segurança, recomenda-se um cluster kubernetes dedicado para rodar o servidor Rancher.**
	- **Não é recomendado rodar workloads neste cluster!**
- O rancher permite importar ou criar clusters

## Rancher API Server

- Provê autenticação (Via provedor externo, LDAP, OAuth)
- RBAC
- Pode criar clusters via GUI
- Facilita o acesso a catálogos HELM
- Organiza namespaces em projetos
- Automatiza deploy a partir de repositórios git

# Requerimentos

- O Rancher deve rodar em um cluster kubernetes
- Caso seja RKE, é obrigatório ter o Docker instalado
- K3s Cluster com HA
	- **2 nós linux, tipicamente VM**
	- Base de dados externa, recomenda-se MySQL
	- 1 Load Balancer
	- Um domínio registrado DNS
- RKE / RKE2 Cluster com HA
	- **3 Nós linux**
		- Os dados do servidor Rancher serão gravados no etcd
		- O etcd requer um número ímpar de nós a fim de possibilitar HA
	- 1 Load Balancer
	- DNS

# Arquitetura

![[Untitled 663.png]]