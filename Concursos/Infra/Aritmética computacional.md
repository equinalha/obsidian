---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-30T10:09:00
Owner:
  - Eduardo Quinalha
---
# Aritmética Computacional

## Representação sinal-magnitude

- Usa o bit mais significativo para representar o sinal e os demais para o valor
- Desta forma, um valor de 8 bits usa o 8o como sinal e os demais para o valor
- 1 → Negativo; 0 → Positivo
- Pouco utilizada, uma vez que o Zero pode ser representado de duas formas diferentes e isso gera problemas de comparação

## Range de dados

Dado uma variável de n bits, para calcular o range de dados possíveis de serem representados é feito da seguinte forma:

$- 2^{n-1}\ a\ 2^{n-1}-1$

## Representação em Complemento de dois

- Esquema de representação mais utilizado
- O bit mais significativo continua sendo representação de sinal (0 → positivo, 1 → negativo)

> [!note] 🔥
> **Macete para o cálculo do complemento de 2 mais rápido:
**Começa a ler o número da direita para a esquerda até encontrar o primeiro bit 1. Mantém-se este bit e todos à direita. Os demais, inverte-se

**Não precisa se preocupar com o bit mais significativo (sinal)

****O mesmo procedimento pode ser utilizado para voltar ao positivo (identificar o número negativo)**

> [!note] 🔥
> Como detectar Overflow:

Sempre que inverter o bit mais significativo (sinal) significa que houve um overflow. A mesma regra serve para soma e subtração

> [!note] 🔥
> Facilitando o cálculo com hexadecimal na prova:
> | **16^2** | 256 |
> | --- | --- |
> | **16^3** | 4096 |
> | **16^4** | 65536 |

# Representação de dados

- ASCII → 7 bits
- ASCII estendido → 8 bits
- UNICODE → 16 bits (pretende-se representar todos os caracteres do mundo)

## Big endian vs Little endian

- Dada uma palavra, a arquitetura define onde ficam armazenados cada parte da palavra
	- Big endian → O byte mais significativo fica no menor endereço de memória
> [!note] 🔥
> **O final (da palavra) está no maior endereço (BIG)**
	- Little endian → O byte mais significativo fica no maior endereço de memória
> [!note] 🔥
> **O final (da palavra) está no menor endereço (LITTLE)**
    ### **Exemplo:**
    Dada a palavra de 32 bits: 0x84F1D6E4
<!-- Column 1 -->
    **Big Endian**

| **Endereço** | **Valor** |
| --- | --- |
| 2000 | 0x84 |
| 2001 | 0xF1 |
| 2002 | 0xD6 |
| 2003 | 0xE4 |

<!-- Column 2 -->
    **Little Endian**

| **Endereço** | **Valor** |
| --- | --- |
| 2000 | 0xE4 |
| 2001 | 0xD6 |
| 2002 | 0xF1 |
| 2003 | 0x84 |
