---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-05T15:04:00
Owner:
  - Eduardo Quinalha
---
# NMAP

## Uso

`nmap [Scan Type] [Options] {target}`

- **Target**
	- hostname: `teste.org`
	- IP
	- redes: `microsoft.com/24`
	- Ranges de IP’s: `10.0.0.0-255`

## Exemplos:

Detecção de serviços e suas versões:`nmap -sV host`

Modo agressivo: `nmap -A host`

Ping scanning, usado para encontrar hosts ativos na rede: `nmap -sP <rede>`

Scanear porta específica: `nmap -p80 <rede ou host>`

Scanear grupo ou range de portas: `nmap -p80, 443 <rede>` / `nmap -p1-200 <rede>` / `nmap -p- <rede> #Todas as portas` / `nmap -pT:22,U:53 <rede> #Especificando protocolo`

Identificar hostnames ativos na rede: `nmap -sL <rede>`

Identificar o SO: `nmap -O <host>`

Identificar 20 principais portas conhecidas: `nmap --top-ports 20 <host>`

# BAS (Breach and Attack Simulation)

- **técnica utilizada para testar a segurança de uma rede, sistema ou até mesmo de uma empresa**
- simula um ou mais ataques cibernéticos para identificar vulnerabilidades e pontos fracos que possam ser explorados em invasões reais.
- Durante a simulação, são utilizadas técnicas e ferramentas que tentam replicar os métodos utilizados por atacantes para acessar informações confidenciais, como senhas, dados de cartão de crédito, informações de clientes e funcionários, e até mesmo o sequestro destes dados.
- **a simulação de ataque pode ajudar a:**
	- **Avaliar a eficácia das medidas de segurança existentes:** a simulação de ataque pode ajudar as empresas a avaliar a eficácia das medidas de segurança existentes e identificar os pontos que precisam ser melhorados
	- **Identificar falhas e vulnerabilidades de segurança: **por meio da simulação de ataque, as empresas podem identificar falhas e [vulnerabilidades](https://www.zup.com.br/blog/gestao-de-vulnerabilidades) em seus sistemas e redes, o que permite que sejam corrigidas antes que atacantes as encontrem e as explorem.
	- **Cumprir as regulamentações: **em muitos setores, as empresas são obrigadas a cumprir regulamentações de segurança. A simulação de ataque pode ajudar a garantir que a empresa esteja em conformidade com essas regras e requisitos legais.
	- **Treinar equipes: **a simulação de ataque pode ser usada para treinar as pessoas colaboradoras da empresa, aumentando sua consciência em relação à segurança e em como proteger os [dados](https://www.zup.com.br/blog/governanca-de-dados) da empresa.
