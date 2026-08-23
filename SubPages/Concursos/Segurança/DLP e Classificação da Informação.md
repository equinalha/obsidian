---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:25:00
Owner:
  - Eduardo Quinalha
---
# Conceitos

- Foco no vazamento de dados
- Privacidade e confidencialidade
- Depende do processo de inventário e classificação da informação
- Aplicações
	- E-mail → Prevenção de malwares, phishing, etc…
	- Network
		- Monitoramento de tráfego
		- Choke points
		- Segmentação de redes
		- Microssegmentação de serviços
		- Segmentação de redes entre servidores de aplicação e banco de dados
	- Endpoint
		- Dispositivo
		- Monitoramento
		- Segregação de dados, tráfego, etc…
		- Capacidade de lidar com o corrompimento do dispositivo, sem que este possa causar algum comprometimento dos dados corporativos
	- Storage
		- Ciclo de vida dos dados
		- Monitoramento contínuo e controle de acesso
		- Mascaramento dos dados
		- Isolamento em camadas
	- Cloud
		- Convívio híbrido com “on-premises”
		- Ferramentas de DLP nativas em cloud
		- Compartilhamento de pastas em modo público
			- Alvo de ataques
			- Existem ferramentas de varredura que podem ser utilizadas tanto para ataques quanto prevenção e detecção

## Técnicas

- Análise de conteúdo de documentos baseado em regras
	- Inspeções regulares
- Baseado em dicionários
- Correspondência exata de dados
	- Pode afetar o desempenho
- Correspondência exata de arquivos
	- Hash
- Correspondência parcial
- Análise estatística
	- IA
	- Machine Learning
	- Pode gerar falsos positivos/negativos

# Classificação da Informação

## **Níveis de classificação das informações**

- A norma não determina os níveis necessários, apenas fala que eles devem fazer sentido no contexto da organização. 
- Uma das formas mais usadas é tratar a informação como confidencial, restrita, de uso interno ou pública.

### **1.Confidencial**

- É o nível mais alto de segurança dentro deste padrão. 
- As informações confidenciais são aquelas que, se divulgadas interna ou externamente, têm potencial para trazer grandes prejuízos financeiros ou à . 
- São protegidas, por exemplo, por criptografia.

### **2.Restrita**

- É o nível médio de confidencialidade. 
- São informações estratégicas que devem estar disponíveis apenas para grupos restritos de colaboradores. 
- Podem ser protegidas, por exemplo, restringindo o acesso à uma pasta ou diretório da rede.

### **3.Uso interno**

- Representa baixo nível de confidencialidade. 
- Informações de uso interno são aquelas que não podem ser divulgadas para pessoas de fora da organização, mas que, caso isso aconteça, não causarão grandes prejuízos. 
- A preocupação nesse nível está relacionada principalmente à integridade da informação.

### **4.Pública**

- São dados que não necessitam de proteção sofisticada contra vazamentos, pois podem ser de conhecimento público. 
- No entanto, sempre cabe lembrar dos outros dois pilares: a disponibilidade e a integridade.