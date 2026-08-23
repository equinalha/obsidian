---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-12-05T16:20:00
Owner:
  - Eduardo Quinalha
---
# IPv4

> [!note] 🔥
> WildMask!

Máscara coringa (wild mask) → Inverte-se todos os bits, para chegar na máscara padrão.
Útil para determinar se há ou não comunicação direta entre os hosts. Onde houver 0´s na WM, os bits dos endereços devem ser iguais. Onde houver 1, não importa.

> [!tip] 💡
> Quando duas ou mais rotas na tabela de roteamento correspondem a um determinado endereço IP de destino, a rota mais específica (ou seja, a rota com a máscara de sub-rede mais longa) é escolhida. Isso é conhecido como "princípio da máscara mais longa" ou "longest prefix matching".
> Por exemplo, se existem as seguintes rotas:
> 
> - 192.168.0.0/16 via 10.0.0.1
> - 192.168.10.0/24 via 10.0.0.2
> 
> E um pacote com destino a 192.168.10.50 chega, a segunda rota será escolhida, pois é mais específica e cobre apenas uma faixa menor de endereços IP.

> [!tip] 💡
> O tamanho máximo de um pacote IPv4 é de **2^16 = 65535 bytes**
Uma vez que o menor cabeçalho IP possível tem 20 bytes, então o maior payload (incluindo cabeçalho da camada de transporte) é de 65515 bytes

[https://protocolodeinfra.com.br/posts/2020/06/ipv4/](https://protocolodeinfra.com.br/posts/2020/06/ipv4/)

## Características

- **Não orientado a conexão**
- Encaminhamento de pacotes nó a nó
- PDU: Pacotes ou datagramas
- **Protocolo não confiável:** Não há garantia de entrega. Este controle deve ser feito pela camada de transporte
- **Não há garantia de payload:** O único checksum existente é do próprio cabeçalho
- **Fragmentação do pacote**
- Critério de entrega de melhor esforço (best effort)
- **QoS não garantido:** Apesar da existência do campo em seu cabeçalho, isto vai depender da configuração desta priorização nos roteadores por onde o pacote trafegar
- **Tamanho máximo do pacote: **65535 bytes

## Cabeçalho

- Cabeçalho de 20 a 60 bytes

![[IPv4 e IPv6 synced block]]

- **VER:** Versão do protocolo IP: 0100 (IPv4) ou 0110 (IPv6)
- **IHL:** Information Header Length - Tamanho do cabeçalho informado em quantidade de palavras de 32 bits
- **Service Type ou ToS:** Tipo do serviço. Permite tratar QoS
- **Total Length:** Tamanho total do pacote (cabeçalho + payload). De 20 a 65535 bytes (vai depender da MTU da camada 2)
- **Id: **Identificação do pacote em caso de fragmentação. Todos os fragmentos de um mesmo pacote possuem o mesmo Id. O sequenciamento vai depender do campo offset
- **Flags:**
	- **1° bit **não é utilizado
	- **2° bit ** flag é o **DF** (Don’t fragment). Na impossibilidade de transmissão do pacote sem fragmentação, o mesmo é descartado e é enviado uma mensagem para a origem
	- **3° bit: MF** (More fragments). É 1 quando existem mais fragmentos do pacote, 0 quando não há fragmentos ou é o último fragmento
- **Fragment Offset: **Posição deste fragmento em relação ao primeiro. Indicado em bytes.
- **TTL**: tempo de vida do pacote em função de quantidade de saltos. Este valor é decrementado a cada roteador por onde passa.
- **Protocol:** Identifica o protocolo da camada superior ou mesmo da própria camada, por exemplo ICMP
- **Checksum: **Referente ao cabeçalho. É recalculado em cada salto, já que o TTL é decrementado
- **Options and Padding: **Agrega informações adicionais no protocolo IP em relação à fragmentação, monitoramento, etc.
	**Principais opções:**
	- **Record Route**: Esta opção permite que um pacote IP grave seu caminho através de roteadores intermediários.
	- **Timestamp**: registra o tempo
	- **Strict Source Routing: **Permite que um remetente especifique a rota exata que um pacote deve seguir
	- **Loose Source Routing: **Especifica lista de roteadores intermediários que o pacote deve visitar, mas não exige que a ordem seja estrita
	- **Router Alert: **Usada para alertar roteadores intermediários de que o pacote requer um tratamento especial.

## Endereçamento e Mascaramento

## Classes

Inicialmente foram previstas 5 classes de endereços IP (A, B, C, D e E)

| **Classe** | **bits iniciais** | **uso** | **faixa (teórica)** | Prática | CIDR |
| --- | --- | --- | --- | --- | --- |
| **A** | **0** | Subredes | 1.0.0.0 a 127.255.255.255 | **10.0.0.0 a 10.255.255.255** | **10.0.0.0/8** |
| **B** | **10** | Subredes | 128.0.0.0 a 191.255.255.255 | **172.16.0.0 a 172.16.31.0** | **172.16.0.0/12** |
| **C** | **110** | Subredes | 192.0.0.0 a 223.255.255.255 | **192.168.0.0 a 192.168.255.255** | **192.168.0.0/16** |
| **D** | **1110** | Multicast | 224.0.0.0 a 239.255.255.255 | **224.0.0.0 a 239.255.555.555** | **224.0.0.0/4** |
| **E** | **1111** | Reservado | 240.0.0.0 a 255.255.255.255 |   |   |

> [!tip] 💡
> **Regra prática para cálculo de número de hosts e subredes:
**$subredes = 2^{ bits1}$
$hosts = 2^{bits 0} - 2$

## FLSM e VLSM

FLSM (Fixed-Length Subnet Mask) e VLSM (Variable-Length Subnet Mask) são técnicas de subdivisão de redes IPv4 em sub-redes, cada uma com suas características específicas. Essas técnicas são utilizadas no processo de design de redes para otimizar a alocação de endereços IP e melhorar a eficiência no uso dos espaços de endereçamento.

1. **FLSM (Fixed-Length Subnet Mask):**
	- **Características:**
		- Sub-redes com máscaras de sub-rede fixas.
		- Todas as sub-redes têm o mesmo número de hosts.
		- Utiliza máscaras de sub-rede uniformes para todas as sub-redes.
	- **Exemplo:**
		- Se uma rede é dividida em sub-redes utilizando FLSM e a máscara de sub-rede é /24, todas as sub-redes resultantes terão exatamente 254 hosts disponíveis.
2. **VLSM (Variable-Length Subnet Mask):**
	- **Características:**
		- Permite o uso de máscaras de sub-rede de comprimentos variáveis.
		- Cada sub-rede pode ter uma máscara de sub-rede diferente, permitindo um uso mais eficiente dos endereços IP.
	- **Exemplo:**
		- Se uma rede é dividida em sub-redes utilizando VLSM, é possível alocar máscaras de sub-rede diferentes para cada segmento com base na quantidade de hosts necessários. Por exemplo, uma sub-rede pode ter uma máscara de /28 (16 hosts), enquanto outra tem uma máscara de /26 (64 hosts).

**Resumo:**

- **FLSM:** Todos os sub-redes têm o mesmo número fixo de hosts e utilizam máscaras de sub-rede uniformes.
- **VLSM:** Permite o uso de máscaras de sub-rede de comprimentos variáveis, o que resulta em sub-redes com diferentes quantidades de hosts, otimizando o uso do espaço de endereçamento.

A utilização de VLSM é mais flexível e eficiente em termos de uso de endereços IP, permitindo um design de rede mais granular e adaptado às necessidades específicas de cada segmento da rede. Essa flexibilidade faz do VLSM uma prática comum em projetos de redes para otimizar o uso do espaço de endereçamento IPv4.

## Multicast

- Transmissão de um datagrama IP para um grupo de hosts (0 ou mais) identificados por um** único IP de destino**
- Mesmo nível de confiabilidade da comunicação unicast, ou seja, Best Effort (sem garantias)
- Não há restrições quanto ao posicionamento geográfico ou número de membros
- Um host pode ser membro de mais de um grupo ao mesmo tempo
- Um host **não precisa ser membro do grupo para enviar mensagens a ele**
- Existem níveis de conformidade de hosts:
	- **Host de Nível 0: **Não são afetados pela atividade multicast
	- **Host de Nível 1:** Participa de alguns serviços multicast mas não consegue participar de nenhum grupo
	- **Host de Nível 2: **Suporte completo a multicast
- Grupos de hosts são identificados pelos endereços IP classe D ( possuem "1110" associados aos quatro bits de mais alta ordem).
	- O endereço 224.0.0.0 não pode ser atrubuído a nenhum grupo, e 
	- 224.0.0.1 á atribuído ao grupo permanente de todos os hosts IP (incluindo gateways)
- Erros:
	- Um datagrama **não é rejeitado por ter um *****time-to-live***** de 1** ( isto é, o *time-to-live* não é automaticamente decrementado em datagramas que chegam e que não sejam reenviados ). 
	- Um datagrama que chegue com um **endereço de grupo em seu campo endereço fonte é descartado. **
	- Um mensagem de erro ICMP (destino inalcançável, tempo excedido, problema com parâmetros)** nunca é gerada em resposta a um datagrama destinado a um grupo de host.**

## IGMP

Usado por hosts para reportar seus participantes de grupo de hosts a roteadores multicast vizinhos.

Parte integrante do IPv4

Utiliza o número de protocolo IP igual a 2

![[Untitled 434.png]]

- Mensagens:
	- Host Membership Query
	- Host MemberShip Report

---

# IPv6

## Endereçamento

- 128 bits
- Supressão de zeros
	- Pode ocorrer apenas uma vez por endereço
```sql
2001.CAFE:04FF:0000:0000:0000:0000:00CC -> 2001:CAFE:4FF::CC
```
- Máscara padrão: /64
- Capacidade de autoconfiguração, independente do DHCP
- Interfaces do tipo link local são utilizadas para autoconfiguração de IP através da troca de mensagens automaticas entre os hosts, permitindo que cada um se configure em um endereço local único
- Zeros à esquerda podem ser omitidos ":" Grupos compostos somente por zero podem ser omitidos "::" Atenção: Somente pode ser omitido um conjunto de zeros por endereço.

## Endereços especiais

- Multicast (FF00::/8)
| FF01::1 | Interface | All-nodes |
| --- | --- | --- |
| FF01::2 | Interface | All-routers |
| FF02::1 | Enlace | All-nodes |
| FF02::2 | Enlace | All-routers |
| FF05::2 | Site | All-routers |
- Link Local
	- Valido apenas para o enlace em que a interface está conectada (não roteia)
	- Atribuido automaticamente
	- FE80::/64
- Não especificado: ::0
- Loopback: ::1
- Transição 6to4: 2002::/16
- Transição teredo: 2001:0000::/32
- Representação de IPv4: ::ffff:<end. IPv4>
	- exemplo: ::ffff:192.168.0.1

## Cabeçalhos

> [!note] 🔥
> **IPv6 NÃO TEM CHECKSUM NO CABEÇALHO!!!

**O controle de erros foi deixado a cargo de outras camadas.

- Mais simples e modular
- Tamanho fixo de 40 bytes
- Apenas 8 campos (em vermelho os que foram mantidos do IPv4)
	- **Versão**
		- 4 bits
		- 0110
	- **classe de tráfego**
		- 8 bits
		- Classificação e priorização de tráfego
		- Equivalente ao ToS do IPv4
	- **Identificação de fluxo**
		- 20 bits
		- Identificação de pacotes pertencentes ao mesmo fluxo de dados que requer tratamento especial
		- Melhora a eficiência  de roteamento
		- Usado para QoS
		- Pode ser utilizado para segurança, por exemplo em criptografia de fluxo
	- Tamanho dos dados
		- Diferente do IPv4, aqui apenas o tamanho dos dados, descontando o cabeçalho IPv6 que é fixo, 40 bytes
	- Próximo cabeçalho
		- Localiza o próximo cabeçalho de extensão ou o cabeçalho da camada superior
	- Limite de salto
		- Similar ao TTL do IPv4
	- **Endereço de origem**
	- **Endereço de destino**
![[IPv4 e IPv6 synced block 1]]
- O fato de possuir apenas 8 campos torna mais eficiente toranando a comutação mais rápida

## Novidades do IPv6

- Suporte ao IPSec nativo
- Não ocorre mais fragmentação nos roteadores intermediários. Fragmentação apenas na origem
	- Se encontrar um segmento que não suporte o tamanho do pacote, o mesmo é descartado e uma mensagem ICMPv6 é retornada à origem
	- é obrigatório liberar mensagens ICMP em IPv6
- Não existe BROADCAST
	- Unicast
	- Anycast
	- Multicast

## Transição

- Pilha dupla
	- Utilização dos dois protocolos de forma simultânea nos dispositivos
	- Antes de transmitir um pacote à um host de destino, o host de origem consulta um servidor DNS para determinar qual versão de endereço IP usará. Se o servidor DNS retornar um endereço IPv4, o host de origem transmitirá um pacote IPv4, caso retorne um endereço IPv6, transmitirá um pacote IPv6.
- Túnel 6to4
	- Quando dois hosts estiverem utilizando IPv6, mas a transmissão entre eles passar por uma região IPv4, será necessário encapsular o pacote IPv6 em um pacote IPv4 quando entrar nessa região e desencapsular o pacote ao sair dela.
	- O núcleo da rede opera em IPv4
	- Os extremos em IPv6
	- O pacote IPv6 é encapsulado dentro do payload do IPv4
	- O campo protocolo do cabeçalho IPv4 leva o valor 41 (29h)
- Tradução
	- Para converter um endereço IPv6 em um endereço IPv4, o endereço associado IPv6 é convertido em um endereço IPv4 extraindo os 32 bits mais à direita.
	- NAT444 ou CGNAT
		- Segunda camada NAT implementada no provedor de acesso

# Protocolos auxiliares

## ICMPv6

- Incorporou funções de outros protocolos como ARP, RARP e IGMP
- Funcionalidades
	- MLD: Multicast listener discovery
	- NDP: Neighbor discovery protocol
	- Path MTU discovery
	- Mobility support
	- Autoconfiguração Stateless: Dispensa o uso do DHCP
- Tipos mais comuns de mensagens:
	- Parameter problem: 
 - *Erroneous header field encountered.*
 *- Unrecognized Next Header type encountered.*
 *- Unrecognized IPv6 option encountered.*
	- Destination unreachable
	- Packet Too Big

## DHCPv6

# Comparativo

| IPv4 | IPv6 |
| --- | --- |
| Endereço de 32 bits | Endereço de 128 bits |
| IPSec Opcional | IPSec obrigatório |
| Implementação restrita de QoS | Campo Flow Label |
| Fragmentação nos roteadores | Fragmentação apenas na origem |
| Campo opcional no cabeçalho | Cabeçalhos de extensão |
| APR utiliza Broadcast | Utiliza Neighbor Discovery |
| IGMP utilizado em grupos locais | Multicast Listener Discovery |
| Broadcast | Multicast e Anycast |
| Endereço configurado manualmente ou via DHCP | Autoconfiguraçõa e descoberta automática |

![[20231029_161614.jpg]]

# ICMP

- Complementar ao IP
- Testes, toubleshooting
- Permite verificação de conectividade entre equipamentos
- Trafega na carga útil do IPv4, após o cabeçalho

![[Untitled 436.png]]

- Principais mensagens:
	- Echo Request – Faz uma requisição para verificar se a máquina está ativa na rede.
	- Echo Reply – Resposta ao comando anterior, confirmando que a máquina está ativa. A troca dessas duas mensagens é o que conhecemos como PING (Packet Internet Grouper).
	- Destination Unreachable – É utilizado quando a rede ou o endereço de host de destino não pode ser alcançado ou encontrado. **Outra utilização menos comum, é quando a FLAG DF (Don’t Fragment) está ativa e o pacote necessita ser fragmentado para passar por redes de MTU menores.**
	- Source Quench – Utilizado anteriormente quando o destinatário necessitava que a origem diminuísse o fluxo de pacotes. Como tal controle atualmente é exercido pela camada de transporte, esse código tem sido pouco utilizado.
	- Redirect – Utilizado para informar que determinado pacote pode ter sido roteado de forma errada.
	- Time Exceeded – Quando o campo TTL chega a 0 e o pacote deve ser descartado. É um sintoma de loop na rede.
	- Parameter Problem – Mensagem ICMP para informar ao emissor da mensagem de que há problemas no cabeçalho IP com parâmetros inválidos.