---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:25:00
Owner:
  - Eduardo Quinalha
---
# Pesquisar

- Varredura TCP FIN

# Cabeçalhos

## Ethernet

- 18 bytes
- Preâmbulo 7 bytes

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## STP

- Adiciona 8 bytes ao cabeçalho ethernet
- Chamado BPDU

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## VLAN

- Adiciona um campo de 4 bytes no cabeçalho ethernet
	- Destes, 2 bytes são utilizados para identificação do campo
	- 3 bits prioridade (QoS)
	- 1 bit indicador de canonicidade
	- 12 bites VLAN Id

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## IPv4

- 20 a 60 bytes
- Checksum do cabeçalho somente
- O campo TOS foi atualizado e hoje chama-se DS → DiffServ

![[Untitled 828.png]]

## IPv6

- Tamanho fixo = 40 bytes

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## TCP

- 20 bytes

![[Untitled 829.png]]

## UDP

- 8 bytes

![[Untitled 830.png]]

## ICMP

![[Untitled 831.png]]

## IPSEC

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## ARP

<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

## ICMP

![[Untitled 832.png]]

## HTTP

<!-- Column 1 -->
![[HTTP-HTTPS synced block]]

<!-- Column 2 -->
![[HTTP-HTTPS synced block 1]]

## SSL

<!-- Column 1 -->
<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

<!-- Column 2 -->
<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

<!-- Column 3 -->
<!-- Failed to import synced block: path failed validation: path.block_id should be a valid uuid, instead was `"undefined"`. -->

# Algoritmos de criptografia e hash

## Simétrico

- Algoritmos: D3ABIT
	- DES, 3DES, AES, Blowfish, IDEA, Twofish

| **Algoritmo** | **Bloco** | **Chave** | **Rodadas** | **Obs** |
| --- | --- | --- | --- | --- |
| DES | 64 bits | 64 bits (56) | 1 |   |
| 3DES | 64 bits | 128, 196 (112. 172) | 3 | Critp / Decript / Cript |
| AES | 128 bits | 128, 196, 256 | 10, 12, 14 |   |
| RC4 | 8 bits | até 2048 |   | Fluxo |
| RC5 | 32, 64 e 128 | até 2048 | até 255 | Bloco |
| RC6 | 32, 64 e 128 | até 2048 | até 255 | Bloco, maior desempenho |

## Assimétrico

- Algoritmos
	- DH, RSA, El Gamal

## HASHES

| **Função** | **Entrada** | **Saída** |
| --- | --- | --- |
| MD5 | Múltiplo de 128 bits | 128 bits |
| SHA1 | 512 | 160 bits |
| SHA256 | 512 | 256 |
| SHA512 | 512 | 512 |

# Certificados ICP-Brasil

| Certificado | Meio Armaz | Validade | Revogação | Obs |
| --- | --- | --- | --- | --- |
| A1 | Software | 1 Ano | 48 / 72h | Não precisa de senha a cada uso, Pode ser copiado |
| A2 |   | 2 Anos | 36/ 54 |   |
| A3 |   | 3 Anos | 24 / 36 | Senha a cada uso |

![[20230810_232711.jpg]]
