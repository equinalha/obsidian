---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:20:00
Owner:
  - Eduardo Quinalha
---
# Correio Eletrônico

- Protocolos
	- Todos eles podem implementar suas respectivas versões seguras, com o uso de túnel TLS/SSL
	- POP3/POP3S
	- IMAP/IMAPS
	- SMTP/SMTPS
- **MUA**: Mail User Agent
- **MTA**: Mail Transfer Agent
	- Atua tanto como cliente como servidor, dependendo do sentido da comunicação
- Recursos adicionais
	- Aviso de entrega e leitura
	- Prioridade de mensagens
	- Possibilidade de agendamento
	- Redirecionamento e mensagens automáticas
	- Envio para múltiplos usuários ou listas de distribuição
- Composição das mensagens
	- Envelope
		- Informações relevantes ao MTA
		- Endereços de remetente e destinatário, aspectos de segurança, priorização
	- Conteúdo
		- Cabeçalho: Informações relevantes ao MUA
		- Corpo: Conteúdo
> [!tip] 💡
> A separação entre Header e Body se dá por uma linha em branco
- MIME
	- Suporte a diversos conteúdos

# SMTP

- Portas:
	- 25/TCP
	- SMTPS **465** com SSL
	- **587** com TLS (STARTTLS)
- Implementação assíncrona
- STORE-AND-FORWARD
- Conexão persistente (várias mensagens em uma mesma sessão)
- Mensagens em ASCII

## ESMTP (Versão estendida)

- Codificação 8BITMIME
- Mensagens em UTF8
- DSN (Delivery Status Notification)
- Autenticação AUTH
- Implementado pipelining
- 1ª mensagem EHLO ao invés de HELO
- Principais mensagens
	- HELO / EHLO
	- MAIL
	- RCPT
	- DATA (início do corpo da mensagem)
	- RSET
	- QUIT

# POP3

- Portas
	- 110
	- **995** (POPS)
- 3 Fases
	- Autorização do usuário
	- Transação - Busca, download, e marcação das mensagens baixadas
	- Atualização - Exclusão das mensagens marcadas
- Autenticação em HASH MD5

# IMAP

- Portas
	- 143
	- 993 (IMAPS)
- Versão atual 4

# Aspectos de Segurança

- Tipos de ataque/ameaças
	- Spoofing de e-mail associado a outros ataques
	- Comprometimento de MTA
	- SPAM
- Spoofing
	- Passos
		1. Atacante se autentica como um usuário qualquer no MTA
		2. Altera ou manipula o campo MAIL FROM
		3. Adapta a mensagem. Funciona em conjunto com PHISHING
- Comprometimento dos MTA’s:
	- Oportunidade para manipulação completa das mensagens por parte dos atacantes
- Segurança nos pares
	- PGP (OpenPGP)
		- Utilizado em ambientes mais simples, menos formais, menos complexos
		- Camada de aplicação
		- Antes da emissão e depois da recepção
		- Utilização de HASH e criptografia: RSA, 3DES e SHA-1
			- Assinatura digital
			- Criptografia da mensagem
		- Utiliza chave de sessão (Criptografada com a chave pública)
	- S/MIME
		- Ambientes corporativos e mais complexos
		- Utiliza codificação MIME
		- Implementado a partir de uma ICP via protocolo X.509

## SPAM

- Relay aberto - MTA sem critérios de segurança
- Proxy aberto (anônimo) - Deep web
- Zumbi SPAM - Bots (máquinas invadidas)
- Técnicas Anti-SPAM
	- Listas de bloqueio (brancas, negras, gray)
	- Filtros/Analisadores de conteúdo (filtros de bayes)
	- Técnicas SPF (Sender policy framework)
	- Técnica DKIM (Domain Keys Identified Email)
	- DMARC (Domain-based Message Authentication, Reporting & Conformance)
	- Gerência da porta 25

### Listas de Bloqueio

- Simples porém eficiente
- Pode ser implementado tanto nos MUA quanto MTA
- Não analisa o conteúdo do e-mail
- As listas são compartilhadas globalmente
- Blacklist
- Whitelist
- Graylist
	- as duas técnicas conjugadas
	- As vezes solicita reenvio de confirmação da origem (interação humana)
	- Aguarda reenvio para liberação

### Analisadores de conteúdo

- Verifica conteúdo e anexos
- Padrões de comportamento
- Semelhante ao IPS
- Alto custo de processamento
- Filtro Bayesiano
	- Aspectos estatísticos
	- Probabilidade para aprendizagem dinâmica
	- Processos estocásticos
	- Redes neurais

### SPF

- Foco no spoofing de e-mail
- Legitimidade do remetente
- Relação de confiança entre domínios

### DKIM

- Domain Key Identified Email
- Usa autenticação com chaves públicas
- Assinaturas digitais entre os MTA`s
- Verifica o cabeçalho e conteúdo

### DMARC

- Tecnologia alternativa ao ANTISPAM tradicional
- Funcionamento em conjunto com o SPF e DKIM

### Gerência da porta 25

- Técnica mais recente
- Amplamente divulgada pelos organismos responsáveis pela segurança na internet
- MTA’s de provedores não possibilitam mais a conexão de clientes pela porta 25, apenas a 587.
- A porta 25 é livre entre MTA’s de provedores conhecidos
- Fases
	- Submissão: Usuário para o provedor
	- Transporte: Entre servidores de e-mail
