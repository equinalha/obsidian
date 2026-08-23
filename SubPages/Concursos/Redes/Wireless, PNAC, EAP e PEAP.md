---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:20:00
Owner:
  - Eduardo Quinalha
---
# Wifi (802.11)

Segue a topologia em estrela, porém tbém é possível comunicação sem base central (redes ad hoc)

(**AB**i**G**ail **N**ão **AC**eitou) - 522255

| **Padrão** | **Banda (Ghz)** | **Canal (MHz)** | **Modulação** | **Antenas** | **Velocidade (Máx)** | **Obs** |
| --- | --- | --- | --- | --- | --- | --- |
| **a** | 5 | 20 | OFDM |   | 54 | Incompatível com o b |
| **b** | 2.4 | 20 | DSSS |   | 11 |   |
| **g** | 2.4 | 20 | OFDM / DSSS |   | 54 | Evolução do b |
| **n** | 2.4 / 5 | 20 / 40 | OFDM | MIMO 4 ant. | 600 |   |
| **ac** | 5 | 40, 80 e 160 | OFDM | MIMO 8 ant. | 7000 |   |
| **ax** | 2.4/5 | 80 | OFDMA | 8x8 DL/UL MU-MIMO | 9.6 GBps | Conceito de “Color” / WPA3 |
| Wifi 6E | 6 |   |   |   |   |   |

O padrão b se sobrepôs ao a devido ao seu alcance cerca de 7x maior

## SSID

O tamanho máximo de um SSID em uma rede Wi-Fi 802.11 varia dependendo da versão do padrão Wi-Fi em uso. Nas versões mais comuns, como 802.11n e 802.11ac, o tamanho máximo de um SSID é de 32 caracteres. Isso inclui letras maiúsculas e minúsculas, números e alguns caracteres especiais. No entanto, é importante observar que a maioria dos dispositivos e roteadores modernos segue esse limite de 32 caracteres, mas alguns dispositivos mais antigos ou menos comuns podem ter limites ligeiramente diferentes.

## Modos de operação

Os dois modos podem operar simultaneamente em uma célula 802.11

### DCF

- **Independe de controle central**
- usa o CSMA/CA
- Forma 1:
	- Antes de enviar, escuta o meio, caso esteja livre envia os dados
	- Enquanto envia, não pode escutar o meio
- Forma 2:
	- Envia um pacote RTS (request to send) para o destino
	- Destino envia um pacote CTS (clear to send) de volta para o emissor
	- Após enviado os dados, aguarda um pacote ACK sinalizando que os dados foram recebidos
	- Se o pacote ACK não for recebido, indica que os dados não foram recebidos e reinicia o processo
- NAV:
	- Network Alocation Vector
	- Uma terceira estação que perceba o tráfego dos pacotes RTS ou CTS estima o tempo da transmissão e não tentará transmitir neste intervalo

### PCF

- **Depende de um controle central**
- Polling

### Intervalos

- SIFS (Short InterFrame Space): Após este intervalo, apenas pacote ACK ou fragmento de pacote que já esteja sendo transmitido
- DIFS (DCF InterFrame Space): Qualquer estação poderá se apoderar do meio
- PIFS (PCF InterFrame Space): Estação central envia pacotes polling
- EIFS (Extended InterFrame Space): Estações podem comunicar a ocorrência de pacotes corrompidos

![[Untitled 494.png]]

## Segurança

A estação central envia periodicamente quadros de sinalização contendo o SSID e Mac Address dela

### Criptografia dos dados

Como trata-se de um meio compartilhado, é necessário implementar criptografia para garantir a confidencialidade dos dados

- **WEP**
	- **Cifra de fluxo RC4**
	- Wired equivalent privacy
	- **chaves estáticas**
	- Utiliza vetores de inicialização IV em conjunto com a chave
	- Foi implementado a TKIP como alternativa para melhorar a segurança
- **WPA (802.11i)**
	- **Cifra de fluxo RC4**
	- **Chaves dinâmicas**
	- Autenticação por 802.1x ou RADIUS
	- TKIP
		- Uma chave de 128 distinta por pacote
		- Uma chave dinâmica é gerada para cada pacote
	- Compatível com WEP
	- Na versão personal, a senha é fixa (versão doméstica)
	- Na versão enterprise, **o 802.1X possibilita que cada usuário possua uma senha de acesso exclusiva**
- **WPA2**
	- **Cifra de bloco AES**
	- 4 Way handshake
![[Untitled 495.png]]
	- TKIP + CCMP

![[Untitled 496.png]]

- WPA3
	- Recompor a vulnerabilidade do 4-way-handshake
	- Evitar ataque de reinstalação de chave
		- SAE - Simultaneous Authentication of Equals
	- Aumento do tamanho das chaves
		- WPA3-Personal - 128 bits
		- WPA3-Enterprise – AES-CCMP 128 bits e HMAC-SHA256
		- WPA3-Enterprise com 192 bits
	- Proteção de dados históricos
		- Caso a senha seja violada, não é possível derivar a chave a partir dela para descriptografar dados já trocados pela rede

## Arquitetura

> [!note] 🔥
> Uma **BSS **pode ser formada por um conjunto de estações, fixas ou móveis, e um AP (Access Point) opcional
> ![[Untitled 497.png]]
> 
> Uma **ESS **é formada por duas ou mais BSSs com APs, interligadas por um sistema de distribuição que normalmente é uma LAN por fio
> 
> ![[Untitled 498.png]]

## Serviços

Uma WLAN deve prover 9 tipos de serviços, divididos em duas categorias:

- **Serviços de distribuição**
> [!note] 🔥
> **[ADeRe DistInte] 
[Associado Distrubui e Integra]**

	- Lidam com a mobilidade das estações a medida que entram e saem das células
	- São eles:
		- **Associação**
			- Usado para conectar-se aos AP’s.
			- O cliente anuncia sua identidade e recursos, se aprovado, passará para a autenticação
		- **Desassociação**
		- **Reassociação**
		- **Distribuição**
			- Determina como rotear quadros enviados ao ponto de acesso
		- **Integração**
			- Faz a conversão dos quadros para o formado da rede de destino
- **Serviços da estação**
> [!note] 🔥
> **[AuDePrivEn]
[Autentica Privada de Dados]**

	- Usados depois que ocorre a associação
	- São intracelulares
	- São eles
		- **Autenticação**
			- **o ponto de acesso envia um quadro de desafio especial à estação móvel, esta
demonstra conhecimento da chave secreta (senha) criptografando o quadro de desafio e transmitindo
de volta ao ponto de acesso. Se o resultado for correto, a estação móvel será completamente registrada
na célula;**
		- **Desautenticação**
		- **Privacidade**
			- Administra a criptografia
		- **Entrega dos dados**

## Tipos de estação

O IEEE 802.11 define 3 tipos de estação, dependendo de sua capacidade de mobilidade dentro da WLAN

- Sem transição:
	- Estação fixa.
	- Pode movimentar-se apenas dentro da mesma BSS
- Transição inter-BSS
	- Pode movimentar-se de uma BSS para outra
	- Apenas dentro da mesma ESS
- Transição inter-ESS
	- Pode movimentar-se de um ESS para outro

# 802.11 ax (Wifi 6)

| 802.11 ax | 802.11 ac |
| --- | --- |
| 1024 QAM (10 bits por símbolo) | 256 QAM (8 bits por símbolo) |
| 8x8 DL/UL MU-MIMO | MU-MIMO |
| BSS Color | - |
| Banda: 80 MHz | 160 MHz |

[https://www.intel.com/content/www/us/en/gaming/resources/wifi-6.html](https://www.intel.com/content/www/us/en/gaming/resources/wifi-6.html)

O **IEEE 802.11ax**, também conhecido como **Wi-Fi 6**, é um padrão de rede sem fio desenvolvido pelo IEEE (Institute of Electrical and Electronics Engineers) para melhorar o desempenho de redes Wi-Fi em ambientes de alta densidade de dispositivos, como escritórios, estádios, e residências com muitos dispositivos conectados.

Aqui estão alguns dos principais benefícios e características do **Wi-Fi 6 (802.11ax)**:

1. **Maior velocidade**: O Wi-Fi 6 oferece velocidades teóricas de até 9,6 Gbps, em comparação com os 3,5 Gbps do Wi-Fi 5 (802.11ac), o que melhora o desempenho geral da rede.
2. **Eficiência em ambientes de alta densidade**: Em locais com muitos dispositivos conectados simultaneamente, como prédios de escritórios, Wi-Fi 6 utiliza tecnologias como **OFDMA** (Orthogonal Frequency Division Multiple Access) e **MU-MIMO** (Multi-User, Multiple Input, Multiple Output), que aumentam a capacidade da rede para lidar com várias conexões ao mesmo tempo sem perda significativa de desempenho.
3. **OFDMA**: Essa tecnologia divide os canais Wi-Fi em subcanais menores, permitindo que o roteador se comunique com vários dispositivos simultaneamente, em vez de ter que alternar entre eles, o que reduz a latência.
4. **MU-MIMO aprimorado**: O Wi-Fi 6 melhora o MU-MIMO (já presente no Wi-Fi 5), permitindo que o roteador se comunique com mais dispositivos ao mesmo tempo tanto no upload quanto no download de dados.
5. **BSS Coloring**: Essa tecnologia ajuda a diferenciar sinais de diferentes redes que operam no mesmo canal, minimizando a interferência e melhorando a eficiência do uso do espectro em ambientes congestionados.
6. **Target Wake Time (TWT)**: Uma função que permite que os dispositivos entrem em modo de espera (sleep mode) e acordem apenas em momentos programados para economizar energia, prolongando a duração da bateria de dispositivos como smartphones e tablets.
7. **Melhor uso do espectro de 2,4 GHz e 5 GHz**: O Wi-Fi 6 melhora o desempenho tanto em frequências de 2,4 GHz quanto 5 GHz, tornando-o mais eficiente em diferentes tipos de ambientes.

## MFP

- O **MFP (Management Frame Protection)** é uma funcionalidade do padrão **IEEE 802.11ax** que visa aumentar a segurança das redes sem fio ao proteger os quadros de gerenciamento contra ataques, como o spoofing e o de desautenticação.

## WPA3

- substitui o protocolo de criptografia **TKIP **(Temporal Key Integrity Protocol) pelo protocolo de criptografia mais seguro **CCMP** (Counter Mode with Cipher Block Chaining Message Authentication Code Protocol)
- utiliza um processo chamado "Proteção contra ataques de dicionário" (Dictionary Attack Resistance) para tornar mais difícil para os atacantes adivinharem senhas por tentativa e erro.
- aprimora o processo de estabelecimento de conexão, tornando-o mais seguro. 
- Isso é feito através do uso do protocolo "Simultaneous Authentication of Equals" (**SAE**), também conhecido como **Dragonfly Key Exchange**. 
- Ele fornece uma maneira mais segura de autenticar dispositivos na rede, **reduzindo a exposição a ataques de força bruta.**
- projetado para ser **compatível com dispositivos mais antigos que suportam WPA2,** permitindo uma transição suave para redes mais seguras. 
- Os dispositivos mais antigos ainda podem se conectar a redes WPA3, mas não se beneficiarão das mesmas melhorias de segurança.

# PNAC (802.1x)

- Proteção de redes via autenticação
- Especialmente útil no 802.11
	- Concessão de uma porta virtual para comunicação
- Participantes
	- Suplicante - Cliente de software em uma estação cliente Wi-Fi
	- Autenticador - Ponto de acesso
	- Servidor de Autenticação - Banco de dados de autenticação:
		- RADIUS
		- LDAP
		- NTLM
- Pode atribuir o usuário à sua VLAN de forma dinâmica, independendo de porta/switch ao qual esteja conectado fisicamente
- Em wireless, provê uma combinação de usuário e senha por usuário, ao invés de uma senha única para o SSID
- A autenticação é centralizada
- Faz uso do EAP para a comunicação entre suplicante e servidor de autenticação
	- Nesta comunicação, o autenticador funciona apenas como um proxy

# EAP e PEAP

[https://www.intel.com.br/content/www/br/pt/support/articles/000006999/wireless/legacy-intel-wireless-products.html](https://www.intel.com.br/content/www/br/pt/support/articles/000006999/wireless/legacy-intel-wireless-products.html)

[https://learn.microsoft.com/pt-br/windows-server/networking/technologies/extensible-authentication-protocol/network-access?tabs=eap-tls%2Cserveruserprompt-eap-tls%2Ceap-sim](https://learn.microsoft.com/pt-br/windows-server/networking/technologies/extensible-authentication-protocol/network-access?tabs=eap-tls%2Cserveruserprompt-eap-tls%2Ceap-sim)

## Portas

- Controladas
	- Pode autorizar ou desautorizar o tráfego dos demais protocolos a depender do resultado da fase de autenticação (autorizado, não autorizado)
- Não controladas
	- Transmite e recebe tráfego de quadros EAP (EAPOL)

## Fases do processo de autenticação

- 1- Inicialização
	- Quando detectado um novo suplicante, a porta é habilitada e colocada no estado não autorizado
	- Neste estado, somente o tráfego 802.1x é transmitido e os demais são dropados
- 2- Iniciação
	- O dispositivo “authenticator” envia periodicamente um quadro EAP-Request para um endereço mac especial no segmento local
	- O suplicante ao receber este quadro especial, responde com sua identificação
	- O dispositivo encapsula a informação e envia para o servidor de autenticação (RADIUS)
- 3- Negociação
	- O servidor de autenticação envia uma resposta para o dispositivo contendo o tipo de autenticação requerida
	- O dispositivo encapsula esta informação em um novo quadro EAPOL e envia ao suplicante
- 4- Autenticação
	- Após terem concordado no método de autenticação, o suplicante envia as informação ao dispositivo que novamente encapsula e envia para o servidor
	- Caso bem sucedida a autenticação o servidor responde com um Accept que novamente é encapsulada e enviada novamente ao suplicante
![[Untitled 499.png]]

## Tipos de autenticação EAP

### EAP-MD5

- Utiliza o algoritmo MD5 para gerar um resumo da senha do usuário.
- Este resumo é então trocado com o servidor de autenticação para validação.
	1. O cliente EAP envia uma solicitação de autenticação para o servidor.
	2. O servidor responde com um desafio, que é um valor aleatório.
	3. O cliente calcula o MD5 da senha do usuário concatenado com o desafio.
	4. O cliente envia o resumo MD5 para o servidor.
	5. O servidor calcula o MD5 da senha do usuário armazenada em seu banco de dados concatenado com o desafio.
	6. O servidor compara os dois resumos MD5.
	7. Se os resumos forem iguais, o usuário é autenticado.
- Não recomendado pois permite que a senha seja derivada
- Não há autenticação mútua

### EAP-TLS

- Fornece **autenticação mútua** baseada em certificados do cliente e da rede
- Usa o **TLS** para o estabelecimento da conexão e troca de certificados
- Depende de certificados do lado do **cliente e do servidor**
- Pode ser uma desvantagem devido a **complexidade de administração dos certificados**

### EAP-TTLS

- Tunneled Transport Layer Security
- Extensão do EAP-TLS
- Autenticação mútua por meio de um túnel criptografado
- A comunicação entre o cliente e o servidor de autenticação é criptografada
- Requer certificados apenas do lado do servidor

### PEAP

- Semelhante ao EAP-TTLS
- Não requer certificado do lado do cliente
- Funciona como uma camada intermediária, encapsulando outro método EAP (EAP-TLS ou EAP-MSCHAPv2) dentro de um túnel TLS seguro
- Encapsula o protocolo EAP (Extensible Authentication Protocol) em um túnel TLS (Transport Layer Security) criptografado. Isso garante a segurança da comunicação entre o cliente e o servidor de autenticação.

![[802.1x_PNAC.png]]

# Segurança em Redes Wireless

## Tipos de Ataque

### **Evil Twin**

- Criação de uma rede falsa que se parece com a rede legítima
- Incentiva os usuários a se conectarem nesta rede e terem seus dados roubados

### **Ataque de desautenticação**

- Envolve o envio de pacotes de desautenticação para um cliente conectado, forçando-o a se desconectar da rede.
- Pode interromper a conexão do usuário foçando ele a conectar-se em um evil twin

### **Ataque de Reaver (WPS Attack)**:

- Explora uma vulnerabilidade no Wi-Fi Protected Setup (WPS) para descobrir o PIN de 8 dígitos do roteador e, consequentemente, a senha da rede.

### **Ataque de Krack (Key Reinstallation Attack)**:

- Explora uma vulnerabilidade na implementação do protocolo WPA2, permitindo que um invasor decifre dados que deveriam ser criptografados.

### **Rougue Access Point**

- Um invasor conecta um ponto de acesso não autorizado à rede para atrair usuários ou comprometer a segurança da rede.

### Fingerprinting

- Técnica usada para identificar e caracterizar um ponto de acesso Wi-Fi com base em seus atributos únicos e padrões de comportamento.
- Pode ser usada tanto para fins legítimos, como segurança e otimização de rede, quanto para fins maliciosos, como ataques direcionados.
- Geralmente envolve a captura e análise de pacotes de dados que são transmitidos de **forma aberta** (não criptografada) pelo AP, especialmente pacotes de **gerenciamento e controle** que fazem parte da operação normal de uma rede Wi-Fi.
- Coleta e analisa diversas características do AP, que podem incluir:
	- MAC Address
	- SSID
	- Taxas de transmissão
		- Pode ser utilizado para identificar o hardware
	- Capacidades de protocolo (WPA2, WPA3)
	- Intervalo de Beacons
		- O intervalo entre os pacotes beacon que um AP emite pode ser característico e ajudar na sua identificação.
		- Esses pacotes são **enviados periodicamente pelo AP** para **anunciar sua presença** e contêm informações sobre as **capacidades da rede, como SSID, endereço MAC, intervalos de beacon, e suporte a diferentes padrões de criptografia.**
	- Solicitações e respostas de probe
		- Pacotes de probe são quadros de gerenciamento que atuam no processo de descoberta e conexão de dispositivos a redes sem fio. 
		- Quando um dispositivo cliente (como um smartphone ou laptop) procura por redes Wi-Fi, ele envia solicitações de probe que podem ser respondidas pelo AP. 
		- A resposta inclui o SSID, taxas de dados suportadas, o tipo de segurança (como WPA2, WPA3), e o endereço MAC do AP.
		- A análise dessas respostas pode fornecer informações valiosas sobre o AP.
	- Configurações de potência de transmissão
- **Aplicações**
	- Segurança
		- Identificar AP’s desconhecidos ou não autorizados na rede, prevenindo ataques como Evil Twin
	- Rastreamento e Análise
	- Ataques
		- Identificação de APs vulneráveis ou específicos
		- Ataques direcionados como desautenticação ou força bruta
- **Tipos**
	- Fingerprinting Passivo
		- O atacante escuta o tráfego sem interferência
		- Captura pacotes transmitidos abertamente
			- Pacotes de gerenciamento
			- Probes
			- Beacons
	- Fingerprinting Ativo
		- o atacante ou analista envia pacotes para o AP ou para os dispositivos conectados à rede, provocando respostas que fornecem informações adicionais.
		- Por exemplo, ele pode enviar solicitações de probe ou pacotes de autenticação para o AP para observar como este responde.
		- Há uma chance maior de ser detectado