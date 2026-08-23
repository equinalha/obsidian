---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-09T17:02:00
Owner:
  - Eduardo Quinalha
---
# Resumo

![[IPSec.png]]

# IPSec

[https://www.icmpconsultoria.com.br/post/o-que-e-e-como-funciona-o-ipsec](https://www.icmpconsultoria.com.br/post/o-que-e-e-como-funciona-o-ipsec)

> [!note] 🔥
> O IPSec utiliza diversos recursos no que concerne a aspectos de criptografia. Utiliza **chaves assimétricas e/ou certificados digitais para garantir a autenticidade** e integridade das partes
envolvidas, utiliza também** chaves simétricas para a confidencialidade dos dados**, além de **funções HASH para integridade dos dados.**

- RFC 6071
- Concorrente com TLS/SSL, porém é possível utilizar os dois em conjunto
- **Nativo e Obrigatório no IPv6**
- Amplamente utilizado em conexões VPN
- Provê
	- Autenticidade → Valida as partes
	- Integridade → Valida o conteúdo (Não ser alterado no caminho)
	- Confidencialidade → Não lido por quem não deve
- Características
	- **Modularidade**
		- Permite que diferentes aspectos de segurança sejam configurados e aplicados conforme necessário
		- pode ser adaptado para diferentes necessidades e ambientes
	- **Serviço de Segurança**
		- O principal objetivo do IPSec é fornecer um conjunto abrangente de serviços de segurança, incluindo **confidencialidade** (através da criptografia dos dados), **integridade** (assegurando que os dados não foram alterados) e **autenticação** (verificando a identidade dos dispositivos que se comunicam).
	- **Nível de detalhe de aplicação de serviços de segurança**
		- O IPSec permite a configuração detalhada de políticas de segurança que podem ser aplicadas a diferentes tipos de tráfego de rede. 
		- Isso abrange desde a aplicação de segurança em nível de pacotes até a definição de regras específicas para a negociação de chaves e algoritmos de criptografia utilizados.
- **Funciona na camada de rede (Modelo OSI)**

![[Untitled 459.png]]

- Prover uma camada de segurança em meio inseguro
- Solução utilizada por diversos serviços
- Extensão do próprio protocolo IP
- **Configurado por diretivas do SO**
- **Suporte a compressão (Não configurado por padrão)**
- Pode ser utilizado em roteadores e switches L3
	- Na prática, qualquer equipamento da camada 3
- **Elementos**
	- **Cabeçalho de Autenticação - AH**
		- Somente uma estrutura: Cabeçalho AH
		- **Autenticidade e integridade (não contempla confidencialidade)**
		- Garantia de origem e integridade (Hash)
		- **Abrange tanto o cabeçalho quanto os dados**
		- **Acréscimo de um cabeçalho posicionado no meio do pacote IP**
		- Ajuda a combater DoS e DDoS, pois, caso o pacote não atenda a regra de autenticação, pode ser descartado
	- **Cabeçalho de encapsulamento do payload - ESP**
		- Supre as três necessidades
			- **Confidencialidade**
			- Integridade
			- Autenticidade
		- **Somente para o payload**
		- Dividido em três estruturas de cabeçalho
			- Cabeçalho ESP
			- ESP Trailer (após o payload)
			- ESP Authentication (após ao payload)
	- **Protocolo de negociação de troca de chaves - IKE**

> [!tip] 💡
> **AH e ESP podem ser implementados de forma isolada ou em conjunto**

# Etapas

1. **Reconhecimento do anfitrião**
	- Um sistema reconhece que um pacote precisa de proteção e deve utilizar IPSec
	- Para pacotes de saída, isso significa que a criptografia e a autenticação apropriadas são aplicadas
2. **Negociação (IKE Fase 1)**
	- os hosts usam o IPsec para negociar o conjunto de políticas que usarão para um circuito seguro
	- Eles também se autenticam entre si e configuram um canal seguro entre eles que é usado para negociar a forma como o circuito IPsec irá criptografar ou autenticar os dados enviados por ele. 
	- Esse processo de negociação ocorre usando o modo principal ou o modo agressivo.
	- A Fase 1 utiliza-se de chaves DH para o compartilhamento de informações e estabelecimento de um canal seguro
![[Untitled 460.png]]
3. **Estabelecimento do Circuito (IKE Fase 2)**
	- configura um circuito IPsec pelo canal seguro estabelecido na IKE Fase 1
	- Os hosts IPsec negociam os algoritmos que serão usados durante a transmissão de dados
![[Untitled 461.png]]
4. **Transmissão IPsec**
	- os hosts trocam os dados reais pelo túnel seguro que estabeleceram
	- As SAs IPsec configuradas anteriormente são usadas para criptografar e descriptografar os pacotes
5. **Terminação**
	- acontece depois que: 
		- um número de bytes especificado anteriormente passa pelo túnel IPsec
		- a sessão atinge o tempo limite
	- os hosts descartam as chaves privadas usadas durante a transmissão de dados

## Associação de segurança - SA

- Primeiro processo no estabelecimento de um tráfego IPSec
- Pode utilizar o AH ou ESP
- Parâmetros
	- SPI (Security Parameter Index)
		- Identificador dos pacotes
	- Endereço IP de destino
		- Pode ser unicast, multicast ou broadcast
		- Na pratica, uma difusão multicast ou broadcast é replicado por várias unicast
	- Identificador de protocolo (ESP ou AH)
![[Untitled 462.png]]

![[Untitled 463.png]]

- Padding → Complemento de informações para que seja atingido um tamanho mínimo do campo
- Tamanho do padding → Indica a quantidade de informação adicionada no padding

## IKE

- Negociação e troca de chaves
- protocolo que permite que dois sistemas ou dispositivos estabeleçam um canal de comunicação seguro
- baseada na troca de chaves Diffie-Hellman
- Fase 1
	- Executada somente uma vez
	- Engloba a SA
	- Troca de chaves (Criptografia assimétrica)
	- Estabelecimento de um canal seguro
- Fase 2
	- O canal seguro já está estabelecido
	- Pode ser executada várias vezes (renovação)
	- Definição do algoritmo de criptografia (simétrica) que será utilizado
		- Atualmente considerado AES como seguro
	- Definição da função de hash a ser utilizada (MD5, SHA-1)
	- Estabelecimento do tempo de vida
		- Expirado o tempo, somente a fase 2 é renovada
- Modos
	- Main Mode
		- Modo padrão
		- Fase 1 completa
	- Agressive Mode
		- Simplificação da fase 1
		- Utilizado quando já existem outras camadas de segurança, não precisa da troca de chaves e negocia-se diretamente as chaves simétricas
	- Quick Mode
		- Sem compressão
		- Sem fase 1

![[IPSec synced block]]

## Modo Túnel

- Implementado pelos elementos intermediários
- Encapsulamento de todo o pacote IP incluindo o cabeçalho
- Inserção de um novo cabeçalho IP que deve ser retirado no destino
- Normalmente usado de Gateway a Gateway

## Modo Transporte

- Nativo do IPSec
- Transmissão direta dos dados protegidos entre os hosts
- Manipulação dos dados diretamente no payload
- **Não manipula o cabeçalho**
- Definido entre os nós de ponta a ponta
- Normalmente utilizado quando dois hosts precisam interagir entre si de forma segura

![[IPSec 1.png]]
