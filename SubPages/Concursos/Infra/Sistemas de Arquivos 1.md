---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-08T09:23:00
Owner:
  - Eduardo Quinalha
---
# Métodos de Alocação

## **Alocação Contígua**

- as unidades de alocação estão na sequência
- Acesso** rápido e eficiente**
- Pode causar **fragmentação externa** e problemas de **gerenciamento de espaço**

## **Alocação Encadeada**

- as unidades de alocação estão dispostas separadamente, porém, na forma de uma lista encadeada
- cada bloco contém um **ponteiro para o próximo bloco**
- o acesso aleatório é **mais lento**, visto que tem que passar de nó em nó
- **Resolve o problema de fragmentação externa**
- Causa naturalmente o problema de **fragmentação de arquivos**, que é o fato do arquivo ser gravado em blocos em regiões aleatórias do disco
- Pode utilizar-se de um FAT que serve para armazenar os ponteiros para os blocos de arquivos.
	- Isso agiliza o acesso direto aos blocos, sem a necessidade de se percorrer a lista iterativamente.
	- Sem uma FAT, é necessário percorrer a lista bloco a bloco
- **Indexada: **uma unidade de alocação funciona como índice para localizar as demais, que encontram-se espalhadas pelo disco
- **I-Nodes:** Todo arquivo está associado a um nó índice, o qual lista os atributos e endereço dos blocos no disco

# Métodos de Acesso

- **Sequencial: **A gravação de novos registros ocorre apenas no final do arquivo;
- **Acesso Direto: **Permite a leitura/gravação de um registro diretamente na sua posição (registros com tamanho fixo);
- **Acesso Direto + Acesso Sequencial: **O acesso direto até um registro determinado, a partir deste ponto o acesso é sequencial
- **Acesso Indexado ou Acesso por Chave: **o arquvio deve possuir uma área de índice onde existam os ponteiros para os demais registros

# FAT

- Sistema de arquivo simples
- Lista encadeada de alocação de clusters
- Pastas e arquivos são registrados da mesma forma, diferindo apenas em um atributo responsável por marcar como pasta
- Sujeito à fragmentação
- FAT12 e FAT16 possuíam limite de arquivos ou pastas gravados na raiz
- Poucos atributos de arquivos
- Composto por 4 regiões:
	- Região reservada
		- Primeiro setor do volume (partição)
		- Setor de boot
		- BPB → BIOS Parameter Block: Registra o tipo de sistema de arquivos e ponteiros para as demais regiões
	- Região de Alocação de arquivos (FAT)
		- Possui duas cópias da FAT (redundância)
	- Região do diretório raiz
		- Somente FAT12 e FAT16
	- Região de dados
		- Onde são gravados os arquivos e pastas
		- Ocupa a maior parte da partição
- FAT32 → Até 4GB

# exFAT

- Também conhecido como FAT64
- Usado em memória Flash

# NTFS

- Os objetos armazenados são registrados na MFT (Master File Table)
- A MFT possui uma estrutura similar a uma base de dados relacional
	- As linhas representam os registros de arquivos
	- As colunas representam os atributos de arquivos
	- Inclui no mínimo 1 entrada para cada arquivo além da própria MFT
	- Os 16 primeiros registros são reservados para os arquivos de metadados que descrevem a própria MFT
	- Estes arquivos de metadados têm seu nome iniciado por `$`
- Com o uso de MBR, existe uma limitação máxima de 2TB
- Via volume dinâmico pode-se utilizar até 256TB (limite do NTFS)
- Via GPT (GUID Partition Table) também é possível tamanhos acima de 2TB
- **Permite nomes com até 255 caracteres. Não permite: /\:*?”<>|**
- Permissões
	- São cumulativas
	- Negar tem prioridade sobre qualquer outra
- Possui recursos de criptografia a nível de sistema de arquivos de forma transparente
- A partir do Windows Vista e Server 2008 foi incorporado o recurso de self healing, dispensando o uso do CHKDSK
- **LFS**
	- Log File Service
	- Logs de recuperação
	- Dividido em:
		- Área de reinicialização
		- Área de log (tamanho infinito)

# EXT

- Bloco: Menor unidade de alocação. Semelhante ao Cluster
	- Tamanhos de 1024, 2048 e 4096
- As informações básicas ficam armazenadas no superbloco, no início do sistema de arquivos, localizado a 1024 bytes do início e tem tamanho de 1024 bytes
- Os metadados são armazenados em inodes
- Ext3
	- Faz uso de journalling
	- Modos de operação:
		- Ordered
			- Journal atualizado no final de cada operação
			- Existe uma pequena perda de desempenho
		- Writeback
			- O journal armazena apenas informações referentes à estrutura do sistema de arquivos
			- Gravado de forma mais ocasional
		- Journal
			- Mais seguro e mais lento
			- O journal armazena informações sobre alterações e também cópia de segurança de todos os arquivos modificados
- Ext4
	- Maior limite de tamanho de arquivos e tamanho de partições
	- Sem limite de número de subdiretórios
	- Checksum do journal
	- Undelete

# Outros

- HFS → Apple
- APFS → Apple, mais recente que o HFS+
- BRTFS
	- Baseado no princípio *cópia em gravação - COW*
	- Desenvolvido pela Oracle para uso no linux
- XFS → Linux. Possui Journalling
- NFS → Rede
- ISO9660 → CD’s
- Joliet → Extensão do ISO9660 (CDFS)