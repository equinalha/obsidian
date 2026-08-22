---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-14T18:16:00
Owner:
  - Eduardo Quinalha
---
[https://blog.grancursosonline.com.br/aspirantes-a-concurso-serpro-2023-dominando-a-resiliencia-de-aplicacoes/](https://blog.grancursosonline.com.br/aspirantes-a-concurso-serpro-2023-dominando-a-resiliencia-de-aplicacoes/)

# Conceitos

- Capacidade de um sistema de se recuperar rapidamente de falhas e continuar a operação de forma eficiente
- Garante disponibilidade e segurança dos sistemas

# Cache

- Armazenamento de dados frequentemente acessados em local de rápido acesso
- Pode funcionar como fallback de dados
- Auxilia na escalabilidade

## Técnicas

### Cache Digests

- Compila um índice de todas as URL's para as quais haja conteúdo armazenado no servidor local de cache e também vizinhos na rede
- Ao receber uma nova solicitação, pesquisa no cache digest a existência ou não de conteúdo armazenado antes de prosseguir com a requisição

### Caching por expiração (TTL)

- Define um prazo de validade para o conteúdo armazenado em cache

### Cache Distribuído

- espalha os dados entre vários servidores de cache em uma rede
- Muitas CDNs utilizam esse modelo para servir conteúdo com maior eficiência.

### Cache hierárquico

- o cache é organizado em vários níveis, com cada nível armazenando diferentes tipos de dados
- geralmente de forma mais granular à medida que se desce na hierarquia. 
- O cache hierárquico pode ser dividido em **cache L1, L2, L3**, etc., sendo que o **L1** é o mais rápido e o mais próximo do cliente, e os caches posteriores armazenam dados menos acessados

### Cache Adaptativo

- ajusta dinamicamente o comportamento de cache com base em padrões de uso e demanda. 
- Ele pode aumentar ou diminuir o tempo de vida de um item em cache dependendo de sua frequência de acesso ou da disponibilidade de recursos.

### Cache de Prefetching

- tenta prever quais dados serão necessários no futuro e os carrega no cache antecipadamente.

# Fallback

- Mudança para um modo alternativo de operação quando ocorre uma falha
- Exemplo: Mudança para um banco de dados secundário
- Implementar fallback requer que a aplicação seja capaz de detectar automaticamente quando um serviço está fora do ar e alternar para a funcionalidade de fallback sem interrupções perceptíveis para os usuários. 

# Circuit Breaker

- Previne a falha em cascata em sistemas distribuídos
- Quando uma falha é identificada o circuito abre interrompendo as chamadas para o componente problemático
- O circuit breaker monitora continuamente as chamadas para um serviço ou dependência externa.
- Ele observa a taxa de falhas das chamadas recentes e decide se deve ou não permitir que a aplicação faça novas chamadas para esse serviço.
- A principal vantagem do circuit breaker é sua capacidade de responder rapidamente a falhas, protegendo o sistema de falhas em cascata e melhorando a resiliência geral da aplicação. 

# Disaster Recovery

- Conjunto de políticas e procedimentos para recuperar a aplicação, infraestrutura e os dados após um desastre
- Inclui:
	- Backup
	- Recuperação de instâncias
	- Estratégias de migração

# Contingência

- Planos desenvolvidos para lidar com eventos não previstos
- Documentação detalhada que descreve os procedimentos a serem seguidos em caso de desastre, incluindo responsabilidades específicas, comunicação interna e externa, e ações a serem tomadas para iniciar a recuperação.
- Envolve ter:
	- Servidores backup
	- Redundância de dados
	- Procedimentos de emergência

# Balanceamento de Carga Global de Servidores (GSLB)

- Distribuição do tráfego de rede entre vários servidores em diferentes locais geográficos
- Isso é feito com base em algoritmos que consideram fatores como carga atual dos servidores, proximidade geográfica dos usuários, tempo de resposta dos servidores, entre outros.

# Site Ativo x Ativo (Active-Active Site Load Balancing)

- Esta abordagem envolve a existência de mais de um site ativo
- todos capazes de receber e processar requisições de usuários
- Em caso de falha de um site, o tráfego pode ser redirecionado a outro
- Com múltiplos sites ativos, a aplicação ganha maior redundância e disponibilidade.
- Os sistemas de balanceamento de carga Ativo x Ativo são configurados para monitorar continuamente a saúde e o desempenho de cada site. 