---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-04T08:00:00
Owner:
  - Eduardo Quinalha
---
# DNS

- Camada de aplicação
- RFC’s 1034 e 1035
- Porta 53 TCP e UDP
	- UDP → Consultas simples (cliente) **PADRÃO**
		- Nem sempre o cliente sabe que a resposta será **maior que 512 bytes.**
		- O servidor trunca exatamente em 512 bytes, então o cliente troca para TCP
	- TCP → Respostas acima de 512 bytes ou **trocas de zonas **(entre servidores DNS)
- **3 tipos de mensagens:**
	- Consulta do cliente para o servidor
	- Resposta do servidor para o cliente
	- Transferência de zonas (atualizações) entre servidores
- **Transferência de zonas**
	- Mestre - escravo
		- Mestre → Detém a informação
		- Escravo → Requisita atualizações
	- **Formas de implementação**
		- AXFR
			- Transferência completa (integral) (A - ALL)
			- Replicação completa da base
			- Alto custo de banda e processamento
		- IXFR
			- Transferência incremental
			- Transfere apenas informações que foram atualizadas desde a última transferência
			- Mais eficiente
	- Zona Raiz ou Root hints
		- Servidores que estão no topo da hierarquia - TLD (Top Level Domains)
		- Possuem endereços amplamente conhecidos e divulgados e cadastrado automaticamente nos servidores de consulta
		- Caso os servidores intermediários não consigam resolver os nomes, transferem a busca para os TLD’s
		- Existem 13 Root Hints que constituem o ROOT DOMAIN
	- Tipos de servidores
		- **Primários:** Mantém as tabelas de configuração localmente
		- **Secundário: **Recebe atualização do primário com as informações sobre zona
		- **Caching-only:** Somente realiza cache dos domínios consultados, sem nenhuma informação adicional, transparente ao mundo externo
- Zona reversa
	- Criado para a resolução em sentido contrário
	- A partir do IP obtêm-se o hostname

## Tipos de consultas

- “Resolver”
	- Aplicação que roda em conjunto ou em separado do cliente
	- Faz a tradução de fato
	- Interage com servidores DNS
- **Tipos**
	- **Autoritativa**
		- Característica de resposta positiva
		- Resposta obtida diretamente pelo servidor responsável pela zona
	- **Positiva**
		- Resposta obtida de um servidor intermediário, a partir de qualquer nameserver
		- Servidores que fazem parte de zonas secundárias
	- **Referencial**
		- Não sabe a resposta mas indica quem sabe
	- **Negativa**
		- Resposta dada pelo servidor autoritativo
		- Registro inexistente ou tipo de consulta incorreta

## Métodos de consulta

- Iterativo
	- O próprio resolver local vai consultando um a um a hierarquia de DNS até encontrar a resposta
- Recursivo
	- A responsabilidade é repassada de um a um na cadeia

![[Untitled 457.png]]

- Modelo híbrido
	- Une os dois métodos anteriores
	- Dentro da rede local, funciona com uma consulta recursiva
	- Normalmente um servidor interno resolve os nomes da própria rede/domínio
	- Na borda externa da rede, um servidor resolve nomes externos
	- Porém ao atingir o DNS na borda, chamado encaminhador, este funciona no modelo Iterativo

## Campos das entradas DNS

- 5 Campos
	- **Domínio**: Nome de domínio usado na pesquisa
	- **TTL** (Opcional): Tempo de vida nos caches
	- **Classe**: Classe do registro, geralmente IN (Internet)
	- **Valor ou Dados:** Valor de fato. Informação que pode ser o IP,  que será dado na resposta
	- **Type**: Tipo de registro
		- **A:** Endereço IPv4 associado
		- **AAAA: **IPv6
		- **CNAME**: Alias, apelido. Aponta para o nome real (não o IP)
		- **PTR**: Tradução reversa. A partir de um IP retorna o nome
		- **NS**: DNS responsável pelo domínio
		- **MX**: Servidor de e-mail relacionado ao domínio
		- **SRV**: Serviços disponíveis em um domínio:
		- **SPF:** tipo de registro DNS TXT que lista todos os servidores autorizados a enviar e-mails de um determinado domínio.
			- Registros DNS TXT serviam para publicar avisos relativos a um domínio, porém evoluíram para outras utilidades
			- se um registro SPF não possui o endereço de IP de um remetente ou domínio em sua lista, o servidor de recebimento não entregará esses e-mails ou irá marcá-los como spam.

```plain text
// Exemplos:

;
; BIND data file for linuxconfig.org
;
$TTL    3h
@       IN      SOA     ns1.linuxconfig.org. admin.linuxconfig.org. (
                          1        ; Serial
                          3h       ; Refresh after 3 hours
                          1h       ; Retry after 1 hour
                          1w       ; Expire after 1 week
                          1h )     ; Negative caching TTL of 1 day
;
@       IN      NS      ns1.linuxconfig.org.
@       IN      NS      ns2.linuxconfig.org.


linuxconfig.org.    IN      MX      10      mail.linuxconfig.org.
linuxconfig.org.    IN      A       192.168.0.10
ns1                     IN      A       192.168.0.10
ns2                     IN      A       192.168.0.11
www                     IN      CNAME   linuxconfig.org.
mail                    IN      A       192.168.0.10
ftp                     IN      CNAME   linuxconfig.org.

;
; BIND reverse data file for 0.168.192.in-addr.arpa
;
$TTL    604800
0.168.192.in-addr.arpa.      IN      SOA     ns1.linuxconfig.org. admin.linuxconfig.org. (
                          1         ; Serial
                          3h       ; Refresh after 3 hours
                          1h       ; Retry after 1 hour
                          1w       ; Expire after 1 week
                          1h )     ; Negative caching TTL of 1 day
;
0.168.192.in-addr.arpa.       IN      NS      ns1.linuxconfig.org.
0.168.192.in-addr.arpa.       IN      NS      ns2.linuxconfig.org.

10.0.168.192.in-addr.arpa.   IN      PTR     linuxconfig.org.


; Define o domínio base como xpto.com.br
; aponta que www.xpto.com.br será um alias para foo.com
$ORIGIN xpto.com.br. www.xpto. IN CNAME foo.com.
```

## SOA

- Start of Authority
- Primeiro registro para determinado nome em uma Zona

## DNSSEC

- Extensão de segurança criada para o DNS
- Proteção contra ataques como cache poisoning e redirecionamento de DNS
- Recursos para garantia de autenticidade e integridade
- Não tem recursos para confidencialidade
- Principais recursos
	- Assinatura digital
		- Garantia da integridade dos dados
		- Cada entrada é assinada com a chave privada e a assinatura é verificada por meio de chave pública
	- Chaves públicas e privadas
		- Utiliza infraestrutura de chaves públicas
	- Validação da origem
		- Valida a origem de um registro, garantindo que ele tenha sido gerado por uma fonte confiável
		- Evita ataques de cache poisoning
	- Respostas autoritativas

## Lista de sufixos

- Os clientes DNS podem utilizar a lista de sufixos para tornar possível o acesso a um servidor utilizando apenas um nome parcial. 
- A lista de sufixos é uma lista de nomes de domínios que é usada pelo cliente DNS para completar nomes parciais que não incluem o nome de domínio completo (FQDN). 
- Quando um nome parcial é enviado para um servidor DNS, o servidor tenta primeiro encontrar um registro correspondente ao nome parcial como um FQDN completo. 
- Se isso falhar, ele tenta completar o nome usando a lista de sufixos.

## RRL

- Response Rate Limiting, é uma técnica usada  para mitigar o impacto de certos tipos de ataques de amplificação de DNS,
- especificamente aqueles que envolvem reflexão e amplificação de DNS.
- visa especificamente consultas para as quais o servidor atua como um servidor autoritativo
- O conceito de "janela" em RRL refere-se a um intervalo de tempo durante o qual o servidor DNS rastreia a taxa de consultas DNS recebidas de um endereço IP de origem específico.
- Se o servidor detectar que um endereço IP de origem está enviando consultas a uma taxa que excede um limite predefinido (o limite de taxa), ele tomará medidas para limitar as respostas a esse endereço IP de origem.

---

# DHCP

## Conceitos

- **Pool de Endereços:**
	- **Intervalo consecutivo completo dos endereços IP possíveis** para uma rede que um servidor DHCP pode atribuir aos dispositivos na rede. 
	- São atribuídos dinamicamente pelo servidor DHCP aos dispositivos quando eles se conectam à rede.
- **Escopo:**
	- Divisão lógica de endereços IP em uma rede que é gerenciada por um servidor DHCP. 
	- Cada escopo tem seu **próprio conjunto de configurações de atribuição de endereços IP e parâmetros de rede**, como máscara de sub-rede e gateway padrão.
- **Superescopo:**
	- Um "superescopo" é uma coleção de escopos DHCP que são agrupados para fins de gerenciamento. 
	- Ele permite que um servidor DHCP **gerencie várias redes lógicas,** cada uma com seu próprio escopo, como uma única entidade.
- **Reserva:**
	- Configuração do servidor DHCP que associa um endereço IP específico a um dispositivo com base no endereço MAC do dispositivo
	- Garante que um dispositivo específico sempre receba o mesmo endereço IP quando se conecta à rede.
- **Concessão:**
	- Período de tempo durante o qual um endereço IP é atribuído a um dispositivo.
	- Após o término da concessão, o dispositivo pode solicitar a renovação do endereço IP. 
	- Podem ser configuradas com diferentes durações para controlar a atribuição de endereços IP na rede.

## Características

- Evolução do **BOOTP **e **RARP**
	- BOOTP → Alocação estática de endereço
- Portas
	- **67/UDP** → Mensagens ao servidor
	- **68/UDP** → Respostas ao cliente
- RFCs 2131 e 2132
- Não impede a utilização de endereços configurados manualmente
- **Possui estrutura hierárquica (opcional)**
	- Pode utilizar servidores intermediários (DHCP relays)
	- Não dependem de estarem na mesma rede
	- Caso o tráfego do dhcp passe por roteadores, é necessário ativar o serviço de agent relay
- Empréstimo (leasing) de endereços, podendo haver reutilização
	- O endereço atribuído fica disponível para aquele MAC address mesmo que este esteja desconectado
	- Caso o tempo de leasing seja ultrapassado, sem conexão, aí sim este IP volta para o pool

## Formas de configuração

- **Manual:** Amarrado ao MAC da estação;
- **Automático: **Conecta 1x na rede e é atribuído um endereço permanente;
- **Dinâmico: **Temporariamente/Periodicamente.

## Processo do DHCP

- 4 Fases básicas - **Fluxo normal**
	- **DHCP DISCOVERY**
		- **Primeira mensagem**
		- UDP Broadcast
		- Origem: 0.0.0.0 (cliente)
		- Destino: 255.255.255.255
		- Descoberta dos servidores DHCP para posterior requisição
	- **DHCP OFFER**
		- Segunda mensagem
		- Enviado para o MAC do cliente
		- É utilizado o campo **YIADDR** (cabeçalho DHCP)
	- **DHCP REQUEST**
		- **Ainda enviado via broadcast** informando qual oferta foi aceita (caso exista mais de um DHCP na rede)
		- Mesmo os servidores não escolhidos saberão da escolha, podendo estes retornarem o IP oferecido para o pool
	- **DHCP ACK**
		- Enviado somente pelo servidor escolhido
		- Envia as demais informações (tempo de leasing, DNS, gateway, etc…)
![[Untitled 458.png]]
- Mensagens adicionais
	- DHCP NACK
		- Mensagem do servidor para o cliente
		- Contexto da rede do usuário mudou
		- Não há confirmação do empréstimo
	- DHCP DECLINE
		- Mensagem do cliente para o servidor
		- Endereço IP já estava em uso
	- DHCP INFORMATION
		- Cliente para o servidor
		- Solicita informações complementares para a configuração local
	- DHCP RELEASE
		- Cliente para o servidor
		- Liberação do endereço IP que não será mais utilizado

## Atualização de DNS

- Esse recurso permite que o DHCP faça** ****atualizações dinâmicas no DNS** em nome dos clientes DHCP. 
- Ou seja, quando o cliente DHCP obtém um endereço IP, o servidor **DHCP pode registrar o nome e o endereço IP do cliente no servidor** **DNS**

# SSH

> [!tip] 💡
> Utiliza dois tipos de chaves: Assimétricas para estabelecimento da conexão, simétricas como chave de sessão

- Suporta protocolos de criptografia, incluindo:
	- AES (*advanced encryption standard*), o *triple *DES e o *blowfish*
- Chaves assimétricas
- Porta 22/TCP
- Versões:
	- SSH1
		- Vulnerável a MITM
	- SSH2
		- Versão utilizada atualmente
- Etapas
	- Estabelecimento da conexão, troca de chaves entre cliente e servidor (assimétricas)
		- Ocorre a troca de chaves de sessão (simétricas)

# FTP

![[20230822_081032.jpg]]

> [!tip] 💡
> FTPS → FTP em cima de tunel SSL/TLS, portas 989 e 990
SFTP → FTP em cima do SSH, porta 22
TFPT → FTP em cima de UDP, porta 69

> [!tip] 💡
> O grande problema do FTP é o tráfego de informações em texto plano, inclusive as credenciais (usuário e senha), podendo ser capturado por uma ferramenta de análise de tráfego como o wireshark

- Portas
	- 21/TCP → No servidor, utilizada para controle
	- 20/TCP → Troca de dados de fato
	- 989/TCP → FTPS
	- 990/TCP → FTPS (dados)
- Modos
	- Ativo
		- Após estabelecida a conexão, o próprio servidor conecta-se na porta subsequente do cliente para envio dos dados, através da porta 20 do lado do servidor
		- Pode haver problema com firewall e outras restrições no lado do cliente
	- Passivo
		- Após estabelecida a conexão pela porta 21, o cliente abre a porta para a conexão de dados
		- Não necessariamente será na porta 20, pode ser outra
		- O servidor vai indicar a porta em que ele aguarda a conexão de dados
- Conexões persistentes na porta 21
- Na porta 20 ou porta de dados do modo passivo, as conexões são abertas e fechadas várias vezes (a cada transferência)
- Modo nativo utiliza autenticação (usuário e senha)
	- Pode-se utilizar hash para a autenticação
- Pode-se utilizar SSL/TLS ou IPSEC para a versão segura
	- Mesmo modelo de certificados do HTTPS
- Existe também a versão SFTP, feito em cima do SSH

## Modos de representação

- Modo ASCII
	- Dados de texto
	- O arquivo é convertido da codificação do host remetente para ASCII 8-bit e posteriormente para a codificação do destino
	- Não adequado para arquivos binários
- Modo imagem (binário)
	- Enviado byte a byte
- Modo EBCDIC
	- Texto simples
	- Codificação EBCDIC
- Modo local
	- Para dois computadores com codificações idênticas
	- Transferência em modo texto sem conversão para ASCII

## Modos de transferência

- Modo fluxo
	- Dado enviado como um fluxo contínuo
	- Processamento da transferência e controlado pelo TCP
	- Nenhum identificador de fim de arquivo é necessário
- Modo de bloqueio
	- Prepara o dado
	- Quebra o dado em vários blocos
		- Cabeçalho
		- contagem de bytes
		- campo de dado
- Modo comprimido
	- Utiliza compressão de dados

## Comandos

- **OPEN → Início da sessão, com a conexão estabelecida**
	- Após abrir a aplicação, utiliza-se o comando open ip_do_servidor
- CLOSE → Encerra a sessão, permanece na aplicação
- BYE → Encerra a sessão e fecha a aplicação
- APPEND → Acrescenta dados a um arquivo no computador remoto
- MPUT, MGET → transmissão de múltiplos arquivos

## Códigos de resposta

- Semelhantes ao HTTP
- 1XX
	- A ação solicitada foi iniciada. Aguardar nova resposta antes de proceder com outro comando
- 2XX
	- Ação completada com sucesso
- 3XX
	- O comando foi aceito, porém aguarda nova instrução
- 4XX
	- O comando não foi aceito e a ação não foi executada
	- O erro pode ser temporário e a ação poderá ser requisitada novamente
- 5XX
	- O comando não foi aceito e a ação não foi executada

## TFTP

- Trivial FTP
- Versão simplificada do FTP
- Utiliza a porta 69/UDP
- Utilizado para transferência de pequenos arquivos
- Modo de transmissão bloqueio (blocos) com blocos fixos de 512 bytes e confirmações pelo próprio TFTP (Porque não tem as confirmações do TCP por baixo)
- Não permite navegação e listagem de diretórios
- Não suporta autenticação e nem criptografia

# TELNET

- Tráfego aberto
- Porta 23/TCP
