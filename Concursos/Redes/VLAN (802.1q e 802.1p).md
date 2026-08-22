---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:26:00
Owner:
  - Eduardo Quinalha
---
# VLAN (802.1q)

> [!tip] 💡
> Uma das grandes vantagens de se utilizar VLAN é a segmentação do domínio de broadcast, reduzindo o tráfego da rede.

Permite a criação de diversas redes locais virtuais em um único meio físico compartilhado.

É necessário a existência de um roteador para a comunição de dispositivos entre VLAN’s (O domínio de broadcast é segmentado)

## **Tipos de alocação**

- **Port-Based (Nível 1):** A VLAN é definida com base na porta do switch. Qualquer dispositivo que venha a se conectar nesta porta, fará parte da VLAN
- **MAC Addr based (Nível 2):** Baseado no MAC Address do dispositivo. Qualquer porta ou switch a que este venha a se conectar, ele estará sempre na mesma VLAN definida para ele.
- **Network Addr Based (Nível 3):** Somente para switches L3. Considera a alocação de VLAN baseada no IP do dispositivo.

## **Tabelas de alocação**

- **VLAN Aberta: **BD único de MAC addrs para todas as VLAN’s
- **VLAN Fechada:** Possui um BD para cada VLAN. Mais seguro
- **VLAN mixado:** Pode utilizar os dois modos anteriores

## **Comunicação entre Switches**

As portas que fazem a ligação entre 2 switches diferentes devem ser configuradas em modo trunk. Desta forma, estas portas agregam o tráfego de todas as VLAN’s, podendo transferir os quadros entre os equipamentos.

![[Untitled 455.png]]

## Como fica o quadro

O protocolo 802.1q especifica a inserção de um campo TAG de 4 bytes no cabeçalho ethernet, entre o endereço de origem e o campo PDU (Type/length).

A inserção deste campo gera a necessidade de recálculo do CRC, gerando novo FCS

Em decorrência desta inserção também, tendo em vista que a MTU da tecnologia ethernet é fixo de **1518 bytes**, faz-se necessário a **redução do tamanho do campo payload de 1500 para 1496 bytes**, compensando assim o crescimento do cabeçalho que normalmente é de **18 bytes** mas com o uso de VLAN sobe para **22 bytes.**

Destes 4 bytes, 2 são utilizados para identificar o campo:
	- 0x8100
	- 0x9100
	- 0x9200

Dos outros 2 bytes:

- 3 bits → Prioridades (0 a 8)
	- Protocolo **802.1p**
	- Não reserva a banda, somente prioriza o envio de pacotes
	- Melhora no tráfego de pacotes com tempos críticos
- 1 bit → Indicação de canonicidade
	- 0 → MAC canônico
	- 1 → MAC não canônico
- 12 bits → Identificador da VLAN
	- Endereços 0 e 4095 são reservados
	- Disponíveis de 1 a 4094

![[VLAN (802.1q e 802.1p) synced block]]

## Q in Q

- É possível "tunelar" VLANs adicionando uma marcação extra, que é conhecida como "Q-in-Q" ou "double tagging". 
- O Q-in-Q é uma técnica de encapsulamento de VLANs em que uma VLAN é colocada dentro de outra VLAN. 
- Isso permite que várias VLANs sejam transportadas em uma única conexão de rede e fornece isolamento de VLAN adicional em ambientes que exigem segurança e gerenciamento de VLAN mais granulares.
- Ao usar o Q-in-Q, um cabeçalho VLAN adicional é adicionado à trama Ethernet original, permitindo que a trama seja transmitida por outra VLAN. 
- O primeiro cabeçalho VLAN (VLAN interna) identifica a VLAN original, enquanto o segundo cabeçalho VLAN (VLAN externa) identifica a VLAN que está sendo usada para transportar a VLAN interna. 
- O equipamento de rede que suporta o Q-in-Q pode ser configurado para adicionar ou remover os cabeçalhos VLAN, permitindo que as VLANs sejam transmitidas por uma rede que não suporta VLANs nativas.

![[VLAN.png]]
