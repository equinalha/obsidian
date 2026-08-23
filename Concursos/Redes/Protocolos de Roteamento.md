---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-22T13:00:00
Owner:
  - Eduardo Quinalha
---
# Roteamento

## Estático (Não adaptativo)

- **Tem prioridade sobre o roteamento dinâmico**
- Também chamado de não adaptativo
- **Não reage às mudanças na rede**
- Principais algoritmos
	- **Dijkstra**
		- busca pelo caminho mais curto independente de  métrica
		- não leva em consideração aspectos lógicos da rede como a largura de banda ou latência dos enlaces de comunicação
	- **Flooding**
		- O roteador encaminha o pacote recebido para todas as demais interfaces
		- Esgota as possibilidades de caminho até o destino
		- Causa overhead na rede
		- **Utilizado em redes wireless**

## Dinâmico (Adaptativo)

- É capaz de **atualizar as informações de sua tabela de forma automática**
- O objetivo do algoritmo é identificar uma árvore lógica de escoamento com os melhores caminhos mapeados
- Os algoritmos de roteamento dinâmico podem ser divididos em duas categorias

### Vetor Distância

- Utiliza um parâmetro de **distância** no qual é possível mapear em uma tabela interna do roteador a distância para determinados destinos
- Os roteadores trocam informações entre si baseado nesta tabela
- Para determinação das rotas, busca identificar a rota de menor custo com base na** quantidade de saltos**
- **Não considera latência, largura de banda e outros fatores de desempenho**
- Simples implementação e manutenção
- Geralmente **não é escalável**
- Principal protocolo: **RIP**

### Estado de Enlace

- Neste método, os roteadores vizinhos trocam entre si informações baseados no **estado dos enlaces conhecidos por eles**
- Sempre que algo muda, a informação é propagada para os demais roteadores
- Cada enlace tem um custo baseado em medidas de desempenho e estado
	- Congestionamento
	- Capacidade de transmissão
	- Entre outros
- **Nem sempre o caminho mais curto será o mais eficiente**
- Principais referências: **OSPF** e **IS-IS**

# RIP

- É um protocolo da **camada de aplicação**
- Utiliza a porta 520/**UDP**
- Foi desenhado para redes pequenas de baixo desempenho
- Utiliza o método** vetor distância**
- Baseado na contagem de saltos com **limite de 15 saltos** para cada rede destino
- É um tipo de protocolo de roteamento interno **IGP**

## Funcionamento

- Para trocar informações, os roteadores **encaminham toda a tabela de roteamento a seus vizinhos**
- Caso o roteador que recebe essas informações detecte possíveis rotas com **quantidade de saltos menores** quando comparado com suas entradas atuais, esse **atualiza suas informações com a nova rota.**
- As tabelas são enviadas **periodicamente de 30 em 30 segundos** aos vizinhos
- O próprio envio das tabelas é considerado como um método de “**keep alive**”
- caso o roteador não receba mensagens do seu vizinho em até 180 segundos, considera-se tal vizinho inativo, portanto, não será considerado rotas que possuam o respectivo roteador como nó de trânsito
- Como a troca de informações reside entre os vizinhos, tem-se que o algoritmo é **descentralizado**
- Caso o roteador possua duas rotas distintas para um mesmo destino com mesmo custo, será realizado de forma automática o **balanceamento de carga **entre as duas rotas através do método** ROUND-ROBIN**
- A convergência da rede pode se tornar lenta à medida que a rede cresce
- Problemas conhecidos
	- loops ocorridos na troca de tabelas com informações inconsistentes
	- Frente a uma falha de um enlace, os roteadores começam a repassar informações inválidas sem considerar a falha no enlace, gerando contagem infinita na quantidade de saltos para a referida rede.
	- Tal problema é conhecido como contagem para o infinito (count to infinity)
	- pacotes destinados à rede inalcançável ficarão vagando na rede sem alcançar o destino, consumindo banda da rede.
	- Técnicas para amenizar este problema:
		- Limitação da quantidade de saltos
		- Split Horizon
			- Evita que o roteador propague a informação de uma rota para a mesma interface de onde aprendeu
		- Route poison
			- Ao se descobrir uma falha em um enlace, a rota para aquela rede é definida com uma quantidade de salto acima do permitido
		- Poison reverse
			- Permite convergência em menor tempo
- Diferenças entre o RIPv1 e RIPv2

![[Concursos/images/Untitled 45.png]]

# OSPF

- Atualmente na versão 3 **com suporte a IPv6**
- Considerado a evolução do RIP
- É um protocolo **IGP** **capaz de operar em redes extensas**
- O OSPF suporta **Equal-Cost Multi-Path (ECMP)**, permitindo que o tráfego seja **distribuído entre múltiplos caminhos de igual custo**, aumentando a eficiência e a redundância.
- Considera custos do link como
	- Largura de banda
	- Congestionamento
	- Atraso
- **Sem limite de quantidade de saltos**
- O OSPF pode implementar roteamento de tipo de serviço **(TOS - Type Of Service)**, que permite diferenciar o tratamento de pacotes com base no tipo de serviço especificado.
- Possui uma visibilidade global da rede com menor troca de mensagens quando comparado ao RIP
- Tempo de convergência menor
- Diferente do RIP que atua na camada de aplicação, **OSPF atua na camada de rede, usando o campo do tipo do protocolo = 80**
	- Todas as mensagens OSPF começam com um **cabeçalho fixo de 24 octetos**, que contém informações essenciais para o processamento do pacote.

## Funcionamento

- Baseado no algoritmo SPF (algoritmo de Dijkstra)
- Como é baseado no estado do link, não armazena todas as informações das possíveis rotas em suas tabelas
- Mensagens
	- LSU (Link State Update)
	- LSA (Link State ACK)
- As mensagens são disparadas em dois momentos
	- Quando o roteador detecta uma alteração na rede
	- A cada 30 minutos
- Permite recursos de autenticação
- Utiliza Multicast, ao invés de broadcast

## Hierarquia

- O OSPF permite o estabelecimento de uma hierarquia dentro do mesmo AS
- Divide-se a área em grupos menores de roteadores
- A divisão em áreas permite
	- Escalabilidade e eficiência do protocolo
	- Reduz a quantidade de informações de roteamento que precisam ser processadas por cada roteador
- Os roteadores dentro de uma área **conhecem toda a topologia daquela área e trocam informações detalhadas sobre as rotas internas.**
- No entanto, entre as áreas, apenas informações resumidas são compartilhadas, reduzindo o volume de dados propagados.

### Estrutura das Áreas

![[Concursos/images/Untitled 46.png]]

- **Área 0 (Backbone)**
	- Principal e obrigatória
	- Todas as demais áreas devem estar conectadas a ela
	- Todo o tráfego entre diferentes áreas deve passar pela **Área 0**
- **Áreas Regulares**
	- Definidas para agrupar roteadores e sub-redes
	- Cada área mantem uma visão interna completa
	- Mas resume esta visão para as outras áreas
- **Áreas Stub e Totally Subby**
	- Áreas que não precisam propagar informações externas (de fora da rede OSPF)
	- Visão simplificada da rede

### Tipos de roteadores

- **Internal Router**: 
	- Roteadores que estão inteiramente dentro de uma área específica e só compartilham informações com outros roteadores daquela área.
- **Backbone Router**:
	- Roteadores que participam da Área 0.
- **Area Border Router (ABR)**: 
	- São roteadores que conectam diferentes áreas e são responsáveis por resumir e propagar informações entre elas.
- **Autonomous System Boundary Router (ASBR)**: 
	- São roteadores que conectam a rede OSPF a redes externas, como outras organizações ou a internet,
	- são responsáveis por redistribuir rotas externas para dentro da rede OSPF.

## Centralização

- O OSPF permite que um roteador seja configurado para atuar em modo centralizado
- Este roteador deverá possuir adjacência física com os demais

# BGP

- Protocolo de roteamento **dinâmico** mais utilizado entre sistemas autônomos (AS) na internet.
- É um protocolo **EGP **que utiliza uma abordagem **baseada em políticas.**
- Atua na **camada de aplicação**, assim como o RIP, na porta 179/TCP
- Ao contrário dos protocolos internos que otimizam rotas com base em **métricas simples** (como o custo no OSPF ou a distância no RIP), o BGP seleciona rotas com base em **políticas configuradas pelos administradores de rede,** o que o torna altamente flexível. 
	- Essas políticas podem basear-se em preferências econômicas, regras de interconexão entre ISPs ou na necessidade de evitar certos caminhos
- Comunicação semipermanente, estabelecendo sessões BGP entre pares de roteadores
- Nestas sessões há o envio regular de mensagens keepalive
- É capaz de tratar máscaras CIDR com grande capacidade de sumarização de rotas
- Utiliza HASH MD5 para autenticação

## Autonomous System (AS)

- conjunto de redes IP e roteadores sob o controle de uma única entidade administrativa
- Cada AS é identificado por um número exclusivo chamado **ASN (Autonomous System Number)**, atribuído por entidades como o IANA (Internet Assigned Numbers Authority) ou os RIRs (Regional Internet Registries).

### Tipos

- **Single-homed AS**: 
	- Conectado a apenas um outro AS. 
	- São, geralmente, redes pequenas que dependem de um único provedor de serviços de internet (ISP).
- **Multi-homed AS**: 
	- Conectado a mais de um AS, proporcionando redundância e resiliência. 
	- Redes grandes, como empresas multinacionais, geralmente utilizam essa configuração para garantir disponibilidade.
- **Transit AS**: 
	- Permite que o tráfego de outros ASs passe por ele. 
	- Provedores de serviços de internet (ISPs) que conectam várias redes atuam como sistemas transitórios.

## Funcionamento

- Um roteador BGP **não envia a tabela de roteamento inteira de uma só vez**, mas utiliza uma **série de atualizações incrementais** conforme a topologia da rede muda.
- Nos anúncios entre os AS’s, apresenta-se políticas de alto nível considerando diversos aspectos de negócio.
- Utiliza o algoritmo VETOR CAMINHO
	- A informação fornece a rota integral até o destino e não somente a métrica, evitando problemas de loop na rede
- De maneira similar ao OSPF, só envia as atualizações quando há alterações na tabela
- Para a aplicação das políticas, os roteadores devem informar alguns de seus atributos específicos juntamente com as informações das rotas

### Atributos de Rotas

- **AS-PATH**
	- Lista os ASs pelos quais um pacote passará.
	- Permite que o BGP **evite loops de roteamento**
	- Também oferece uma maneira de **influenciar a seleção de rotas** com base no número de ASs que um caminho precisa atravessar.
- **NEXT-HOP**
	- Interface de saída pela qual será enviado o pacote
	- Especifica o próximo salto para atingir a rede de destino.
- **LOCAL_PREF**:
	- Indica a preferência por uma rota em comparação a outras.
- **ORIGIN**
	- Fonte originária das informações de roteamento

## Convergência

- O BGP é conhecido por sua **convergência lenta** em comparação a outros protocolos
- pode demorar para que todas as mudanças na topologia sejam propagadas e aplicadas globalmente
- No entanto, isso também faz com que o BGP seja mais estável

### Segurança

- O BGP, por ser crítico para o funcionamento da internet, enfrenta desafios de segurança. 
- Um dos problemas mais comuns é o **BGP hijacking**, quando um AS malicioso anuncia prefixos IP que não lhe pertencem, redirecionando ou interrompendo o tráfego. 
- Para mitigar esses problemas, surgiram iniciativas como o **RPKI (Resource Public Key Infrastructure)**, que autentica o AS proprietário de um prefixo IP.

## Escopos

### iBGP

- Dentro de um mesmo AS
- Nos roteadores de borda que se comunicam com múltiplos AS
- Troca de informações destes roteadores com possíveis redes alcançáveis por estes
- Há o estabelecimento de apenas uma sessão lógica entre eles, sem necessidade de conexão física
- É obrigatório a criação de uma sessão entre todos os roteadores iBGP em uma rede lógica FULL.

### eBGP

- Comunicação entre AS diferentes
- É necessário conexão física