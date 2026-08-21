![[Tarefas.base]]

>[!col]
>[[Prompt Engineering]]
>[[Curso Kubernetes 4 Linux]]
>[[Cursos Gitlab]]
>[[Certidões]]
>[[Concurso MPPR 2025 - Fiscalização]]
>[[GitOps Introduction with Argo CD – Erwin's Blog!]]
>
>[[Formação DevSecOps Alura]]
>[[Formação Alura Backend]]
>[[Trabalhando com issues curtas]]
>[[GitLab Flow]]
>[[Mágicas do git]]
>[[OAuth 2.0 & OpenID]]
>

### To Learn …
> [!col]
>>[!col-md]
>>- [ ] ELK stack
>>- [ ] MidPoint
>>- [x] ArgoCD / GitOps
>>- [x] Minio
>>- [x] n8n
>>- [x] External Secrets
>
>>[!col-md]
>> - [ ] ELK stack
>> - [ ] MidPoint
>> - [x] ArgoCD / GitOps
>> - [x] Minio
>> - [x] n8n
>> - [x] External Secrets
>
>>[!col-md]
>>- [ ] Kubernetes / Helm
>>- [ ] Dynatrace
>>- [ ] DNS / Bind
>>- [ ] Syslog
>>- [ ] Keycloak
>>- [ ] Vsphere
>>- [ ] Curl
>>- [ ] Certificados / OpenSSL

[https://www.elastic.co/pt/kibana](https://www.elastic.co/pt/kibana)
[https://hclsoftwareu.hcltechsw.com/](https://hclsoftwareu.hcltechsw.com/)
[https://mppr.mp.br/Pagina/Feriados-2025](https://mppr.mp.br/Pagina/Feriados-2025)
# Contatos COOPE

| **Coordenação de Operações – COOPE** |               |                   |
| ------------------------------------ | ------------- | ----------------- |
| **Coordenador**                      |               |                   |
| **Moisés de Gois Pires**             | **3250-4945** | **41 99641-2449** |
| **Equipe**                           |               |                   |
| Eduardo Quinalha                     | **-**         | 41 98417-6057     |
| Gilberto Froes de Aguiar Júnior      | 3250-4945     | 41 99914-5131     |
| Izilbert Oliveira da Silva           | 3250-4036     | 41 99712-2490     |
| Oduvaldo Vick Neto                   | -             | 11 99462-1018     |

# DevOps Roadmap

## Learn the Fundamentals First

Before you even touch fancy automation tools, make sure you actually understand the stuff you’ll be automating. That means:

- Linux basics (file system, processes, permissions, services)
- Networking (IP, DNS, HTTP/S, ports, routing, NAT, firewalls)
- System administration (users, groups, package management, logs)
- Bash scripting for automating simple tasks
- Basic Python scripting (log parsing, API calls, automation scripts)

## Version Control and CI/CD Are Core Skills

- Jenkins
- GitLab CI
- GitHub Actions
- CircleCI

## Containers and Orchestration

Start with **Docker**:

- Build images with Dockerfiles
- Use volumes and networks
- Work with multi-container apps via Docker Compose

**Kubernetes** (K8s):

- Pods, deployments, services
- ConfigMaps and secrets
- Scaling and rolling updates
- Ingress and service discovery

You’ll also want to understand managed K8s services like AWS EKS, Azure AKS, or GCP GKE.

## Cloud Skills

- Compute (EC2)
- Networking (VPC, subnets, security groups)
- Storage (S3, EBS)
- IAM (roles, policies, least privilege)

Then, learn how to deploy containers or Kubernetes clusters in the cloud.

## Infrastructure as Code (IaC)

This is how you make cloud resources repeatable and version-controlled. **Terraform** is the most popular and works with all major clouds.

Learn how to:

- Define infrastructure in .tf files
- Use variables and modules
- Apply and destroy infrastructure safely
- Store state securely

## Observability

- If you build and deploy something but can’t see when it’s failing, you’re not doing DevOps.
- Prometheus + Grafana for metrics
- ELK stack (Elasticsearch, Logstash, Kibana) for logging
- Cloud-native tools like AWS CloudWatch or GCP Stackdriver

## Security (DevSecOps Basics)

Security is now a core part of DevOps, not an afterthought. Learn to:

- Scan code for vulnerabilities (Snyk, Trivy)
- Manage secrets (Vault, AWS Secrets Manager)
- Secure Docker images
- Apply IAM best practices

## Build Real Projects

Don’t just follow tutorials. Build something end-to-end, like:

- A microservice app with Docker
- CI/CD pipeline → Docker → Kubernetes → Cloud deployment
- Terraform for infra provisioning
- Monitoring + logging setup
- Push everything to GitHub with a README that explains your setup.

## Network With the Community

Join DevOps communities:

- Reddit (r/devops, r/kubernetes, r/aws)
- CNCF Slack channels
- DevOps Discord servers
- Local meetups or conferences
- Ask questions, share your progress, and help others.

## Stay Consistent & Keep Learning

DevOps tools evolve fast. Even once you land a job, you’ll keep learning. Read blogs, watch KubeCon talks, experiment in your home lab.

If you start from zero and commit a few hours per week, you could be job-ready in 6–8 months. The key is not to try and master everything at once — build layer by layer, and make sure each new tool you learn connects to something you already understand.

If you want a well-structured course & resource suggestions to follow this roadmap step-by-step, DM me and I’ll share what worked for me and others breaking into DevOps.

---

```bash
export DT_URL="https://dependencytrack.mppr.mp.br"
export DT_API_KEY="odt_jm3CqjMN_BKlqquQZmg8lIDMbP1SMpyhAlz93wET8"
export PROJECT_NAME="disis-epromp-judicial-backend"
export KEEP_VERSIONS="desenvolvimento homologacao producao"
PROJECT_DATA=$(curl -s -H "X-Api-Key: $DT_API_KEY" "$DT_URL/api/api/v1/project?name=$PROJECT_NAME")
echo "$PROJECT_DATA" | jq -c '.[]' | while read -r project; do
	VERSION=$(echo "$project" | jq -r '.version');
	UUID=$(echo "$project" | jq -r '.uuid');
	DELETE=true;
	for keep in $KEEP_VERSIONS; do
		if [ "$VERSION" = "$keep" ]; then
			DELETE=false;
		fi;
	done;
	if [ "$DELETE" = true ]; then
		echo "🗑️ Deletando versão órfã: $VERSION ($UUID)...";
		curl -s -X DELETE -H "X-Api-Key: $DT_API_KEY" "$DT_URL/api/api/v1/project/$UUID";
	else
		echo "✅ Mantendo versão oficial: $VERSION";
	fi;
done
```

```bash
# mudando rede padrão do docker

sudo systemctl stop docker

# Editar o arquivo principal de configuração do Docker, que é o /etc/docker/daemon.json ou criar um com o conteudo:

{
  "bip": "172.31.0.1/16",
  "default-address-pools": [
    {
      "base": "172.31.0.0/16",
      "size": 24
    }
  ]
}

sudo systemctl start docker
```
