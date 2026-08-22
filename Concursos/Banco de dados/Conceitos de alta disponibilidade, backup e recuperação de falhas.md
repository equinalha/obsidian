---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:07:00
Owner:
  - Eduardo Quinalha
---
# Alta Disponibilidade (HA)

## Principais pontos de falha

- Servidor de BD incluindo (SGBD) e sua plataforma de hardware e software
- Banco de dados físico
	- Mídias de armazenamento
	- Interfaces de HW e SW
- Links
	- Conexões externas
	- Redes

## Cluster de HA

- Visa prestar um serviço contínuo, especialmente sob falha de algum componente
- Failover
	- Ao detectar uma falha o sistema automaticamente comuta para o modo desastre
	- Neste modo, normalmente, um servidor secundário assumirá o papel do master
	- Quando o servidor primário normalizar, ocorre a operação de failback
- Formas de se obter HA
	- Backup Online
	- Replicação

## Backup Online

- Proteção contra falha de mídias
- Fornece uma maneira de restaurar um banco de dados físico ao seu estado consistente mais atual.
- Backup contínuo sempre ativo
- Registra as alterações efetivadas no banco
- Utiliza Journal
- Backup Offline
	- Restaura o banco para uma versão anterior
	- Há perda de dados
- Não possui um processo muito rápido de recuperação após uma falha. Há necessidade de recuperar o backup inicial e aplicar as informações presentes no journal para garantir a volta ao estado consistente anterior a indisponibilidade.

## Replicação

- Espelhamento das informações em um servidor secundário
- Fornece um segundo ponto de acesso aos dados
- **Provoca alguma indisponibilidade no serviço**
- O servidor primário envia alterações efetivadas para o servidor secundário, que espelha as mudanças em seu banco de dados
- O servidor secundário está disponível para acesso do cliente, em modo de somente leitura
- Caso o banco de dados primário fique indisponível, a recuperação pode restaurá-lo a partir do banco de dados secundário ou pode simplesmente mudar o processamento para o banco de dados secundário.

# Backup

- Backup
	- Hot → Com o banco em operação
	- Warm
	- Cold → Com o banco desligado. Garante a consistência dos dados
- Tipo
	- Full
	- Incremental → Armazena apenas as diferenças entre o último backup full ou incremental e o momento presente
	- Diferencial → Armazena apenas as diferenças entre o último backup full e o momento presente
- Windows
	- Janela de backup
	- Intervalo de tempo utilizado para a execução do backup
- Job
	- Pode ser agendado para realizar o backup
- Online
	- Online = Hot
	- Offline
	- Offsite → Envia para outro ambiente
- Opções
	- Compressão
	- Deduplicação
	- Encriptação
- Fazendo um backup offline / cold
	- Desativar a instância do BD
	- Copiar os dados
		- Arquivos de parâmetros
		- Arquivos de controle
		- Arquivos de dados
	- Reiniciar a instância

# Recuperação

## Estados de transações

O SGBD mantem um log de transações

- **Ativas**: Iniciadas mas sem commit
- **Acabadas**: Commited
- **Abortadas**: desde o último checkpoint - Rollback

## Rollback

- Rollback de transações (undo):
- Rollback em cascata

## Recuperação baseada em log

Uma entrada de *log* normalmente contém várias peças de informação, sendo uma delas o **identificador de item de dados** (como o endereço de memória ou localização no disco onde o dado está armazenado), outra é a **operação realizada** (exemplo: WRITE) e também os valores antigo e novo. Além disso, inclui-se o identificador único da *transação* que realizou a operação. No entanto, o identificador de item de dados e o identificador exclusivo da transação são conceitos distintos e não devem ser confundidos.

O identificador exclusivo da transação é um **ID de transação** que serve para rastrear todas as operações realizadas por uma mesma transação. Isso permite que o sistema de gerenciamento de banco de dados (SGBD) possa desfazer (rollback) ou reexecutar (redo) operações de uma transação específica, o que é crucial para a manutenção da integridade dos dados em situações de recuperação após falhas.

## Recuperação com atualização adiada (RAA) - Só escreve depois do commit

- Depende do protocolo usado no controle de concorrência
- Como o commit ocorre depois da transação concluída, as transações interrompidas não precisam de UNDO
- Protocolo de duas fases, bloqueio antes da execução até o commit
- Utiliza duas listas de transações: Acabadas desde o último checkpoint e ativas
- Aplica o REDO em todas as operações write_item das transações acabadas, em ordem cronológica
- Transações ativas não acabadas são canceladas e deverão ser re-submetidas

## Recuperação com atualização imediata (RAI)

- Undo/No-Redo
	- Quando consegue se garantir que as transações que terminaram após o último checkpoint foram gravadas
- Undo/Redo
	- Desfaz as transações interrompidas em ordem inversa do log
	- Refaz as demais transações que ocorreram após o checkpoint na ordem do log

## Paginação em Sombra

A paginação em sombra, também conhecida como paginação "shadow", é uma **técnica de recuperação de falhas **em bancos de dados que oferece **alta disponibilidade** ao manter um estado consistente do banco **mesmo em caso de falhas no disco ou outros tipos de erros.** Essa técnica funciona através da criação de cópias "sombra" das páginas de dados do banco, que são utilizadas para restaurar o estado do banco a um ponto anterior em caso de falha.

### **Funcionamento Detalhado:**

1. **Cópia de Páginas:** No início de cada transação, o sistema cria uma cópia da página de dados original, armazenando-a em uma área separada do disco como uma "página sombra". Essa cópia captura o estado consistente da página antes de qualquer modificação ser feita pela transação.
2. **Modificações na Página Sombra:** Durante a transação, todas as modificações nos dados são feitas na página sombra, enquanto a página original permanece intacta. Isso garante que a página original sempre contenha um estado consistente do banco, mesmo que a transação falhe posteriormente.
3. **Registro de Transações:** As informações sobre as modificações feitas na página sombra também são registradas no log de transações do banco de dados. Este log fornece um histórico completo de todas as operações realizadas no banco, permitindo que o sistema restaure o estado do banco a qualquer ponto no tempo.
4. **Recuperação de Falhas:** Em caso de falha no disco ou outro tipo de erro que corrompa a página original, o sistema pode utilizar a página sombra e o log de transações para restaurar o estado do banco a um ponto anterior à falha. Isso garante que o banco de dados possa ser recuperado rapidamente e com perda mínima de dados.