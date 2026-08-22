---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-03T21:35:00
Owner:
  - Eduardo Quinalha
---
# Conceitos

> [!tip] 💡
> Há uma diferença entre recuperação de falhas e tolerância a falhas
**O Backup é uma ferramenta de recuperação, mas não de tolerância**

- Disponibilidade
- Integridade
- Recuperação de falhas

# Políticas de backup

- Técnicas e ações que devem ser executadas para garantir a disponibilidade dos dados, conforme diretrizes estabelecidas
- Quais dados estão sujeitos a backup?
- Restrições associadas a perdas de dados e respectivos impactos
- Frequência destes backups
- Prazo de recuperação
- Responsáveis pela execução e acompanhamento

# Boas práticas de backup

- Diferentes locais
- Correlação direta com os planos de continuidade de negócio da organização
- Oportunidades no contexto de nuvem

## Regra de backup 3-2-1

- **3 cópias **(pelo menos)
	- Original
	- 2 backups
- **2 tipos de mídia** independentes
- **1 cópia remota **(ou offline)
	- Disaster recover

# Tipos de backup 

- **Normal (Full, total)**
	- Recuperação rápida
	- Baseada no backup mais recente
	- Grande volume dedados
	- Marca os arquivos como backupeados
- **Incremental**
	- Somente o que mudou desde o último backup full ou incremental
	- **Marca os arquivos como backupeados**
	- Não gera redundância
	- Complexidade de restauração
- **Diferencial (cumulativo)**
	- Os backups diferenciais são uma estratégia eficaz quando se lida com dados que sofrem alterações frequentes e são de grande valor.
	- Arquivos novos ou modificados desde o último backup completo
	- **Não marca os arquivos**
	- Acumula toda a diferença durante os dias que se passam desde o último backup full
	- Ná prática, ele não enxerga os backups diferencias anteriores e sempre faz o backup de tudo que mudou desde o último full
	- Para a recuperação, basta o último backup diferencial + último full
- **Cópia**
	- Copia os arquivos selecionados
	- Não realiza a marcação de backup
	- Usado como backup “extra”
	- Não realiza a marcação para não interferir no ciclo normal de backup
- **Diário**
	- Arquivos criados ou modificados no dia do back
	- Não realiza a marcação
	- Mesmo comportamento do diferencial
- **Delta**
	- armazena a diferença entre as versões correntes e anteriores dos arquivos. 
	- Este tipo de backup começa a partir de um backup completo e, a partir daí, a cada novo backup são copiados somente os arquivos que foram alterados enquanto são criados hardlinks para os arquivos que não foram alterados desde o último backup. 
	- Esta é a técnica utilizada pela Time Machine da Apple e por ferramentas como o rsync.

# Outros conceitos

- Pool de armazenamento
	- Agrupamento de discos físicos em um volume lógico
	- Virtualização de armazenamento
- Schedule
	- Rotinas
	- Execução de scripts
- Retenção
	- Prazo para guarda dos backups
- Snapshot
	- Estado da VM ou disco
	- Ponto específico no tempo
	- Executdo a quente

# Deduplicação

- Eliminar dados duplicados
- Aplicável a grandes volumes de dados
- Foco em eliminação de redundâncias
- Essa comparação pode ser feita em nível de arquivo, bloco ou sub-bloco, dependendo da tecnologia utilizada.
- Forma de compressão de dados
- Substitui as duplicatas por links simbólicos, ponteiros para o arquivo original
- A deduplicação exige o gerenciamento de metadados, que são informações sobre os dados armazenados, como localização da cópia original, tamanho e outras informações relevantes.
- **Classificações**
	- Deduplicação de Origem
		- Remove a redundância em ambiente de produção, antes mesmo de ser enviado para backup
		- Consome processamento do servidor
	- Deduplicação de Destino
		- Realizado no storage
		- Post-processing
		- Consome banda da rede
- **Tipos de Deduplicação:**
	- **Deduplicação de nível de arquivo:** Identifica e elimina arquivos duplicados, mesmo que estejam armazenados em diferentes pastas ou volumes.
	- **Deduplicação de nível de bloco:** Identifica e elimina blocos de dados duplicados dentro de um mesmo arquivo.
	- **Deduplicação de nível de sub-bloco:** Identifica e elimina sub-blocos de dados duplicados dentro de um mesmo bloco.

# Estratégias de Rotação

- Garantem a retenção e ciclo de substituição dos backups

## GFS (Grandfather-Father-Son)

- Envolve três níveis de backups: diário (Son), semanal (Father), e mensal (Grandfather)
- **Son (Diário)**: Backups diários são feitos e mantidos por um curto período, geralmente uma semana.
- **Father (Semanal)**: No final de cada semana, um backup é promovido a "Father" e é mantido por várias semanas.
- **Grandfather (Mensal)**: No final de cada mês, um backup é promovido a "Grandfather" e é mantido por meses ou até anos.

## Torre de Hanoi

- Cria um padrão de rotação que maximiza a diversidade de backups com um número mínimo de operações
- Minimiza o número de backups necessários para manter um histórico extenso de versões.
- O primeiro backup é feito em uma mídia (ou local), o segundo em outra, e assim por diante
- A complexidade do ciclo aumenta com o número de backups, mas garante que os backups mais antigos sejam substituídos com menos frequência, preservando históricos mais longos.

## FIFO

- Estratégia simples onde o backup mais antigo é sempre sobrescrito pelo mais novo.
- Cada backup substitui o mais antigo, garantindo que apenas um número fixo de backups esteja sempre disponível.
- Ideal para sistemas onde o histórico de versões é menos crítico, e a prioridade é ter apenas os backups mais recentes.

## Backup Diário Semanal (Ciclo semanal)

- Rotação semanal, com um backup diário e um backup semanal que substitui o anterior.
- Um backup é realizado todos os dias da semana (de segunda a sexta).
- O backup de sexta-feira é mantido por uma semana antes de ser sobrescrito.

## Ciclo de Backup 10 (Ciclo de Backup Completo e Incremental)

- Envolve a criação de backups incrementais e completos em um ciclo de 10 dias.
- A cada 10 dias, um backup completo é realizado.
- Nos dias intermediários, backups incrementais são feitos.
- O backup completo mais antigo é sobrescrito a cada novo ciclo de 10 dias.

## Backup Rotacional (Round Robin)

- As mídias são numeradas e usadas em sequência (ex: fita 1 na semana 1, fita 2 na semana 2, etc.).
- Após um ciclo completo, a mídia mais antiga é reutilizada, sobrescrevendo o backup anterior.

## Regra 3-2-1 Combinada com Rotação

- Mantém três cópias dos dados (uma off-site), utiliza dois tipos de mídia e segue um padrão de rotação como GFS.
- Isso garante redundância e recuperação de desastres, além de um histórico de versões.
