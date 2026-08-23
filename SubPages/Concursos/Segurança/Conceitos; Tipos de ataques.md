---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-01T16:00:00
Owner:
  - Eduardo Quinalha
---
# Motivações

- Demonstração de poder
- Financeiras
- Ideológicas
- Comerciais

# Teams, Pentest

- Red Team → Time de ataque. Pentesters, contratados para testar a robustez da rede
- Blue Team → Time de defesa. Equipe de SI
- Pentest
	- Black Box → Nenhuma informação sobre o ambiente, cliente ou sistemas. Utiliza o princípio da obscuridade
	- White Box → Fornecimento das informações do ambiente ao pentester. Possibilita pular a etapa de identificação. Acelera o processo.
	- Gray Box → Intermediário. 
- **Reconhecimento**: Coleta de informações sobre o alvo, incluindo endereços IP, tecnologias e configurações de segurança.
- **Exploração**: Busca de vulnerabilidades conhecidas ou descoberta de novas vulnerabilidades para permitir a entrada no sistema ou rede.
- **Gaining Access**: Comprometimento do sistema ou rede através de técnicas como engenharia social, exploração de vulnerabilidades ou ataques de força bruta.
- **Mantendo Acesso**: Instalação de backdoors, persistência e evasão de detecção para manter o acesso ao sistema ou rede.
- **Escalada de Privilégios**: Aumento dos privilégios do invasor para acessar recursos e informações mais valiosas.
- **Coleta de Informações**: Roubo ou espionagem de informações confidenciais ou sensíveis.
- **Exfiltração**: Transferência das informações coletadas para um local externo ao sistema ou rede comprometidos.

# Varredura de redes

- Identifica portas abertas, serviços rodando, versões de sistemas operacionais
- Permite identificar vulnerabilidades

# Hardening

- Fechar portas
- Desabilitar serviços desnecessários

# MITM - Man In The Middle

- Não necessariamente interrompe o circuito entre duas entidades
- Pode ser utilizado para ataques do tipo REPLAY, onde as chaves de sessão são extraídas e utilizadas para outras transações
- Pode ser utilizado para impedir que as mensagens cheguem ao destino
- Pode ou não haver quebra de confidencialidade

# ARP Spoofing / ARP Poisoning

- Busca-se assumir a identidade de outro host na rede para interceptação do tráfego
- ARP Spoofing atua ativamente no processo do ARP Request, respondendo ser dono de um IP que não é dele
- ARP Poisoning adultera a tabela ARP do switch
- Permite implementar um MITM

# Smurf

- Redirecionamento de tráfego com base em adulteração de endereço IP
- Usa IP Soofing
- Objetivo: Atacar a disponibilidade da vítima
- Envia uma solicitação ECHO-REQUEST para um endereço de boradcast, a partir de um IP Falso. 
	- Os roteadores irão distribuir os pacotes para os diversos destinatários que irão responder para o IP falso, que é a vítima

# Sniffing

- Interceptação de táfego
- Wireshark, TCPDump
- Pode ser maliciosa ou legítima
- Muito efetiva para tráfego sem criptografia
- Depende de configuração nas placas de rede
	- Nativamente as placas vêm configuradas para desencapsular somente pacotes direcionados a ela
	- Modo promíscuo → rede com fio
	- **Modo monitor → rede sem fio**

# Brute Force

- Método de tentativa e erro
- Vale para quebra de criptografia
- Capacidade de ataque diretamente proporcional à capacidade de processamento
- Valem-se de ataques de dicionário
	- Palavras conhecidas e variações
	- Padrões de teclado
- Contramedidas
	- Senhas aleatóreas
	- Cofres de senhas
	- Captcha
	- PAM
		- Uso de senhas de sessão
		- Similar ao CyberArk

# Phishing

- Clonar página legítima para roubo de informações
- A página é falsa. Pode ser detectado por análise da URL ou certificado
- Associado a meios de divulgação como e-mails, mensagens instantâneas
- Spear Phishing
	- Especialização da técnica
	- Direcionado a uma pessoa, público ou órgão específico

# Pharming

- A URL acessada é a legítima, porém a requisição é encaminhada para uma página falsa
- Normalmente faz uso de DNS poisoning ou cache poisoning

# DoS e DDos

- Comprometimento da Disponibilidade
- no caso do DDoS, a taxa de sucesso é alta
- Soluções de contorno dependem das operadoras de acesso a internet
- **DRDoS ou DDoS refletor**:
	- Combinação de DoS, botnet e Smurf Attack
	- A rede de bots envia uma requisição com IP forjado para destinos legítimos que respondem todos ao IP da vítima
	- O ataque na prática acaba saindo de usuários legítimos
- Contramedidas
	- CDN
		- Reduz a carga
		- Tráfego multicast que onera muito pouco a origem
	- Superestimar recursos de rede e processamento → Muito custo com osciosidade
	- Análise de padrões de tráfego - IA
		- Reação automática
		- Pode gerar falso positivo
	- Encaminhamento do tráfego para “buracos negros” (rotas nulas)
	- Hardening de sistemas
	- Ações contratadas com a operadora
		- Bloqueio de tráfego

# Amplificação

**O que é um servidor NTP mal configurado e passível de amplificação?**

Um servidor NTP é considerado mal configurado e passível de amplificação quando aceita determinados comandos, como ou , que permitam gerar respostas muito maiores que a pergunta, para origens forjadas.

Caso esteja acessível à toda a Internet via UDP, esse serviço pode ser explorado para ataques DDoS que usem amplificação. Isso ocorre porque o atacante envia uma requisição forjando o IP da vítima e o servidor com NTP aberto retorna uma resposta muito maior que a requisição.

# Engenharia Social

- Enganação ou observação da vítima em seu meio social
- **Técnicas**
	- **Vishing:** Via telefone
	- **Phishing**
	- **Hoax**
	- **Whaling:** Altamente direcionado com vistas a ludibriar executivos do alto escalão de uma organização

# Ransomware

- Sequestro de dados
- Criptografia dos dados
- Este tipo de ataque demanda tempo e planejamento
- Depende de outros tipos de ataque: malwares, backdoors, etc…
- O atacante demanda um valor de resgate para os dados

# Fingerprinting de redes Wireless

No processo de auditoria de redes sem fio, o fingerprinting ativo de um access point refere-se a uma técnica usada para **identificar o modelo e a versão do firmware** de um access point. Essa técnica envolve o envio de pacotes de sondagem para o access point e a análise das respostas recebidas. O objetivo é identificar as vulnerabilidades conhecidas do modelo e da versão do firmware do access point, a fim de explorá-las em ataques subsequentes.

# SYN Flood

Os **ataques de SYN flooding** caracterizam-se por apresentarem um **grande número de requisições de conexão (pacotes SYN)**. O volume elevado dessas requisições faz com que o **servidor se torne incapaz de respondê-las**. A pilha de memória, dessa forma, acaba "estourando" (overflow) e, consequentemente, **as conexões de usuários legítimos são desprezadas**.

# Eavesdropping

Bisbilhotar. O atacante monitora o tráfego (normalmente em aberto), armazenando informações relevantes para proferir outros tipos de ataque.

Diferentemente do [man-in-the-middle](https://pt.wikipedia.org/wiki/Ataque_man-in-the-middle), o ataque por eavesdropping só intercepta e armazena as informações, não sendo possível modificar tais informações e depois enviá-las para o destinatário original, o que dificulta aos atacados, identificarem que estão sendo atacados e que suas informações estão sendo roubadas.

Como o ataque por *Eavesdropping* não modifica a informação, nem o fluxo normal desta, o ataque por eavesdropping é um ataque passivo a informação.

# Wardriving

- Normalmente feito a partir de um automóvel
- Busca por redes wifi abertas

# Rogue AP

- Iclui um Access Point pirata na rede para enganar os usuários

# DNS Spoofing

- **Mesma coisa que DNS cache poisoning**
- Modificação dos registros com objetivo de redirecionar a vítima para um site fraudulento
- Possibilidades
	- Uso do ARP para apontar para um DNS fraudulento
	- Alteração do registro do DNS de uma zona autoritativa
	- **Exploiting Time-To-Live (TTL)**
		- Manipulação do TTL do registro fraudulento para que o mesmo persista por mais tempo
- Prevenção
	- Usar DNSSEC
		- Respostas com garantia de integridade e autenticidade, porém não tem confidencialidade
	- Usar servidores DNS confiáveis
	- Usar criptografia na comunicação com o servidor DNS (DNSCrypt)

# SynFlood

- É uma forma de DoS
- Envia uma sequência de requisições SYN para o alvo, causando sobrecarga direta da camada de transporte e indireta da camada de aplicação
- Pode ocorrer devido à implementação errada do protocolo TCP
- Normalmente feito com IP´s forjados (spoof) para que o atacante não receba de volta os ACK´s
- Contramedidas
	- SYN Cookies
		- Máquinas SUN e Linux
		- Recurso oferecido diretamente pelo Kernel
		- `echo 1 > /proc/sys/net/ipv4/tcp_syncookies`
		- O sistema passa a responder ao pacote SYN inicial com um cookie, que identifica o cliente. Com isso, o sistema aloca espaço para a conexão apenas após receber o pacote ACK de resposta, tornando o ataque inefetivo.
	- Não é possível apenas limitar o número de conexões por minuto, pois o efeito seria o mesmo do ataque bem sucedido

# Ping of Death

- Tipo de DoS
- Envio de pacotes de ping de tamanho elevado, em alta frequência
- Normalmente o tamanho máximo permitido 65535 bytes
- Causa estouro de buffer