---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-30T10:09:00
Owner:
  - Eduardo Quinalha
---
# Definições e funções

- Combinação de várias unidades
- Criação de uma unidade lógica
- Acesso transparente
- Ganho de performance
- Aumento de capacidade
- Pode ser implementado via
	- Hardware
		- Menor consumo de CPU
		- Maior performance
	- Software
		- Maior flexibilidade

# Tipos

| **Nível** | **Conceito** | **Ganho** | **falha** | **Mínimo de discos** | **Capacidade** | **Desempenho de Leitura** | **Desempenho de Escrita** |
| --- | --- | --- | --- | --- | --- | --- | --- |
| RAID 0 | Stripping | Performance | 0 | 2 | n | Melhorado | Melhorado |
| RAID 1 | Mirror / hot swap | Redundância | 1 disco | 2 | n/2 | Melhorado | Indiferente |
| RAID 4 | Paridade | Performance e Redundância | 1 disco | 3 | n - 1 | Melhorado | Melhorado |
| RAID 5 | Paridade distribuída | Performance e Redundância | 1 disco | 3 | n - 1 | Melhorado | Melhorado |
| RAID 6 | Dupla paridade distribuída | Performance e Redundância | 2 discos | 4 | n - 2 | Melhorado | Melhorado |
| JBOD | Concatenação  | nada | 0 | 2 | n | Indiferente | Indiferente |

- RAID 0
	- Gravação e leitura paralelo
	- Maior desempenho
	- Stripping
	- Não há redundância
	- Não costuma ser utilizado de forma isolada em servidores
	- Duplica o risco, pois a perda de um dos discos implica em perda da totalidade dos dados
![[Untitled 745.png]]
- RAID 1
	- Mirror
	- Redundância e resistência a falhas
	- Maior desempenho na leitura
	- **Mesmo desempenho de escrita**
	- Hot Swap
	- Perda de capacidade de armazenamento (n/2)
- RAID 10 / 01 (1+0 / 0+1)
	- Mínimo de 4 discos
	- Perda de 50%
	- Aumento de performance de leitura
	- Utilizado em sistemas com muitas operações de gravação
	- Pode suportar a falha de até 2 discos (dependendo de quais)
		- De forma cruzada
![[Untitled 746.png]]
- RAID 5
	- Agrega performance e redundância
	- Suporte a falha de até 1 disco
	- Strip set com paridade
	- Bits de paridade **distribuídos** em todos os discos
	- Mínimo 3 discos
	- Perda de 1 disco (equivalente) para o armazenamento de paridade
- RAID 50 (5 + 0)
	- Primeiro o stripping depois o RAID 5
	- Mínimo de 6 discos
	- Pode falhar até 1 disco por conjunto de RAID5
- RAID 6
	- Dupla paridade
	- Suporta falha de 2 discos
	- Mínimo de 4 discos
	- Perda de armazenamento de 2 discos
- JBOD
	- Concatenação de vários discos em uma única unidade lógica
	- Ganho de capacidade
	- Distribuição a nível de arquivos
