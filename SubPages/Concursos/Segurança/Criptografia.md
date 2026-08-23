---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:25:00
Owner:
  - Eduardo Quinalha
---
# Técnicas

- Substituição
	- Cifra de césar
	- Foco na chave
- Transposição
	- Embaralhamento da própria mensagem original (os caractéres não são substituídos)
	- Foco no processo  e não na chave
- Esteganografia
	- Esconder uma informação dentro de outra

# Métodos de decifragem

- Direto
	- Busca obter a chave
- Força bruta
- Dicionário

# Crifragem de bloco

- Depende de armazenagem em buffer
- Utiliza blocos de tamanho fixo
- Há uma perda de performance
- Busca-se garantir a confidencialidade, mas também é possível autenticidade e integridade
- Exemplos:
	- PGP
	- SSL/TLS
	- DES
	- 3DES

## ECB (Eletronic Code Book)

- Método simples
- Independência dos blocos (cada bloco pode ser descriptografada independentemente)
- Alta performance
- Um erro em um bloco não se propaga para os demais
- Pontos fracos
	- Não é seguro por conta da repetição
	- Suscetível a comportamentos padrões de dados

## CBC (Cipher Block Chaining)

- Método mais utilizado
- Utiliza operações XOR
- A cifragem de cada bloco depende de **todos** os blocos anteriores
- O texto em claro do bloco atual passa por uma operação XOR com o texto cifrado do bloco anterior
- **Depende da recepção dos blocos de maneira sequencial**
- Um erro em um dos blocos propaga-se para todos os subsequentes
- Vetor de inicialização
	- **pseudo aleatóreo**
	- Precisa ser conhecido pelas duas partes
	- Funciona como o resultado da cifragem de um bloco zero para então subsidiar a cifragem do primeiro bloco de fato
![[Untitled 300.png]]

## CFB - (Cipher Feedback)

- Muito utilizado
- Suporta qualquer tamanho de entrada, independente do bloco
- Muito usado para aplicações com transmissão imediata
- Similar ao CBC
- O XOR é feito na saída do processo de cifragem

![[Untitled 301.png]]

![[Modos_de_criptografia.png]]

# **Cifragem de fluxo**

- Não necessita agaurdar o processamento de toda a mensagem
- Mais dinâmico e ágil
- Aplicação de forma contínua
- Pode ser bit a bit ou byte a byte

# Princípio de Kerckhoffs

> [!tip] 💡
> A segurança da criptografia tem que estar na chave e força do algoritmo. **O algoritmo deve ser público!**

# Conceitos de Shannon

- **Difusão:** Tornar o relacionamento estatístico entre o texto claro e o cifrado o mais complexo possível
- **Confusão:** Tornar o relacionamento entre o texto cifrado e a chave o mais complexo possível

# Criptografia Simétrica

- Mesma chave
- Mais performático que a assimétrica
- Como boa prática, utiliza-se compressão antes da encriptação
	- Reduz a redundância de dados
	- Dificulta a criptoanálise
	- Diminui o tamanho dos dados de entrada, consequentemente aumenta o desempenho
- Em regra geral, as chaves são menores do que as de criptografia assimétrica
	- de 64 a 256 bits
- A grande desvantagem da criptografia simétrica é a troca de chaves
- Principais Algoritmos (**D3ABIT**)
	- **D**ES
	- **3**DES
	- **A**ES
	- **B**lowfish
	- **I**DEA
	- **T**wofish

|   | **DES** | **3DES** | **AES** | **Blowfish** | **Twofish** | **IDEA** |
| --- | --- | --- | --- | --- | --- | --- |
| **Bloco** | 64 bits | 64 bits | 128 bits | 64 | 64 | 64 |
| **Chave Bruta** | 64 bits | 128 e 192 bits (2 ou 3 chaves) | 128, 192 ou 256 bits | 32 a 448 bits | 128 a 256 bits | 128 / 256 |
| **Chave Efetiva** | 56 bits | 112 e 168 bits (2 ou 3 chaves) | 128, 192 ou 256 bits (10, 12 ou 14 rodadas) |   |   |   |
| **Conceitos** | S-BOX | S-BOX | 3 etapas de substituição, 1 permutação | Redes de Feistel 16 rodadas | Redes de Feistel 16 rodadas | Redes de Feistel, permutas e operações matemáticas |

## DES

- Base para a criptografia simétrica
- Implementa os dois principios de Shannon: Confusão e Difusão
- Cifra de bloco
- Bloco: 64 bits
- Chave: 64 bits
	- 56 → Chave propriamente dita
	- 8 bit → Paridade
- Atualmente já quebrado por força bruta
- Utiliza substituição e permutação
- Utiliza conceito de S-BOXES (box de substituição)
- Utiliza o conceito de rede de FEISTEL (Cifra de FEISTEL)
- A partir da chave principal, geram-se chaves parciais
	- Cada sub-chave tem 48 bits (é feita uma expansão)
- Dois processos separados que se cruzam periodicamente
	- Graficamente, assemelha-se ao DNA
	- São 16 rounds
- Processo:
	- O bloco de 64 bits é dividido em 2 blocos de 32 bits
	- Um bloco será processado e o outro não
	- A chave de 56 bits é derivada em 16 chaves de 48 bits
	- O bloco que será processado é expandido em 48 bits para coincidir com a chave
	- Este bloco é processado pela S-BOX, resultando num bloco de 32 bits
	- O bloco processado é permutado (P-BOX), via XOR com o outro bloco
	- Por fim eles trocam de posição e então inicia a próxima etapa
![[Untitled 302.png]]

![[DES.png]]

## 3DES

- Tentativa de sobrevida do DES
- 3 Rodadas do fluxo principal
- Etapas
	- Criptografia DES → Primeira chave
	- Criptografia reversa (Descriptografia DES) → Segunda chave
	- Criptografia DES → Terceira chave
- Existe uma variante que utiliza apenas duas chaves, A e B
	- Criptografia DES → Chave A
	- Criptografia reversa (Descriptografia DES) → Chave B
	- Criptografia DES → Chave A
- Força da criptografia
	- 3 Chaves
		- 3 chaves de 56 bits → 168 bits
	- 2 Chaves
		- 2 chaves de 56 bits → 112 bits
- **Desvantagens**
	- Inicialmente, o DES foi projetado para rodar em **hardware**, sua implementação em software é lenta
	- Consequentemente o 3DES é 3 vezes mais lento em software, do que o próprio DES
	- Outra desvantagem é a utilização de blocos de 64 bits. Levando-se em conta a eficiência,** blocos maiores são desejáveis**.

![[3DES.png]]

## Rivest Cipher - RC

- Versões: 4, 5 e 6
- RC4
	- **Cifra de Fluxo**
	- Orientado a byte (bloco)
	- **Chave variável de até 2048 bits**
	- Baseado em permutação randômica
	- **Muito utilizado no TLS**
	- Favorece o tráfego (UDP, mídia)
	- Sequências pseudoaleatórias
- RC5
	- **Cifra de bloco**
	- Blocos de tamanhos variáveis (32, 64 e 128 bits)
	- Chave variável até 2048 bits
	- Quantidade de rodadas variável (até 255)
	- Processo
		- Expansão
		- Encriptação
		- Decriptação
- RC6
	- **Cifra de bloco**
	- Acrescenta a inclusão de multiplicação de inteiros e registradores de 4 bits
	- Maior desempenho

![[Rivest_Cipher.png]]

## AES - Advanced Encryption Standard

- Principal dentro da criptografia simétrica
- pode ser implementado tanto **em hardware quanto em software.**
- Substituto do DES
- Bloco fixo de 128 bits
- Chaves variáveis: 
	- 128 bits - 10 rodadas
	- 192 bits - 12 rodadas
	- 256 bits - 14 rodadas
- Não utiliza FEISTEL
	- Utiliza RJINDAEL
- 3 estágios de substituição
- 1 estágio de permuta
- Estrutura básica
	- SubBytes → Utiliza S-BOX para substituição byte a byte
	- ShiftRows → Permutação simples
	- MixColumns → Combinação linear
	- AddRoundKey → XOR bit a bit com parte da chave expandida

![[Criptografia_Simtrica.png]]

## Blowfish

- Alta velocidade, segurança e flexibilidade
- Blocos de 64 bits
- Tamanho de chave variável: 32 a 448 bits
- Emprega rede de Feistel complexa com 16 rodadas
- Combina operações lógicas e matemáticas com XOR, adição e substituição
- **Aplicações comuns do Blowfish:**
	- Criptografia de arquivos e pastas.
	- Segurança de dados em redes.
	- Proteção de senhas e informações confidenciais.
	- Autenticação de usuários e dispositivos.
- ** O Blowfish pode ser vulnerável a ataques de força bruta se a chave for muito curta.**

## Twofish

- Sucessor do blowfish
- Funciona com blocos de 128 bits
- Chaves de 128 a 256 bits
- Emprega rede de Feistel complexa com 16 rodadas
- Combina operações lógicas e matemáticas com XOR, adição e substituição

## IDEA

- Blocos de 64 bits
- Suporta chaves de 128 bits (IDEA original) e 256 bits (IDEA NX)
- Combina diferentes técnicas criptográficas, como redes de Feistel, permutações e operações matemáticas.

# Criptografia Assimétrica

- Soluciona o problema de troca de chaves por canais inseguros
	- Não necessita de um canal seguro para a troca de chaves
- A depender da necessidade, elas podem ser utilizadas para fins diferentes:
	- Pública → Criptografa / Privada → Descriptografa
	- Pública → Descriptografa / Privada → Criptografa
- Predominância de transposição (permuta) em detrimento de substituição
- Sempre geradas aos pares
- **A obtenção da chave privada a partir da chave pública é computacionalmente inviável**
	- **Atenção!!! Não é impossível, mas computacionalmente inviável devido ao tempo gasto para cálculo de todas as possibilidades**
- Base para assinatura e certificação digital
- Formas de uso
| Aplicação | 1a Chave | 2a Chave |
| --- | --- | --- |
| Confidencialidade | Pública | Privada |
| Autenticidade | Privada | Pública |
- Principais algoritmos
	- Diffe-Hellman - DH
	- RSA
	- El Gamal

| **Algoritmo** | **Tamanho de Bloco** | **Tamanho da Chave** | **Observações** |
| --- | --- | --- | --- |
| Diffie-Hellman (DH) | - | 1024-4096 bits | Troca de chaves segura, não criptografa diretamente mensagens. |
| RSA | Varia (comumente 1024-4096 bits) | 1024-4096 bits | Criptografia de chave pública, amplamente utilizado, vulnerável a ataques de força bruta e fatoração. |
| ElGamal | Varia (comumente 1024-4096 bits) | 1024-4096 bits | Criptografia de chave pública, similar ao RSA, porém menos utilizado. |
| DS (Digital Signature Standard) | - | 1024-4096 bits | Assinatura digital, garante integridade e autenticidade de mensagens, vulnerável a ataques de colisão. |

## Diffie-Hellman - DH

- **Chaves 1024-4096 bits**
- Principal algoritmo para troca de chaves simétricas em meio inseguro
- Baseado em logaritmo discreto em um corpo finito. Este problema é considerado difícil para grandes números primos.
	- Pode ser utilizado em conjunto com curvas elípticas
- **Não é utilizado para criptografar/descriptografar o conteúdo**
	- Em vez disso, ele é usado para gerar uma chave secreta que pode ser usada para criptografar mensagens usando um algoritmo de chave simétrica, como o AES.
- Combinando a chave privada de um lado com a pública do outro, chega-se numa chave que será idêntica à gerada do outro lado, com as informações inversas
- Esta chave será utilizada para troca das mensagens

## RSA

- Principal algoritmo de criptografia assimétrica atualmente
- Utilizou como base o DH
- **Amplamente utilizado em SSL e TLS**
- **Fatoração de números extensos, envolvendo fatores primos → Geração das chaves**
	- A segurança do RSA depende da dificuldade de fatorar grandes números primos.
- Utiliza Função φ de Euler ou Função Totiente de Euler
	- Associa a cada inteiro positivo "n" a quantidade de inteiros positivos menores do que "n" que são coprimos (primos entre si) com "n". 
- **Chaves de 1024, 2048 e 4096 bits**

## El Gamal

- Cálculo de logaritmos discretos em corpos finitos
- **Chaves 1024-4096 bits**
- Transferências de assinaturas digitais e trocas de chave
- O ElGamal combina um algoritmo simétrico para criptografar a mensagem com um algoritmo assimétrico para criptografar a chave simétrica.
- **Base para o PGP e  S/MIME.**
- Assinatura digital de e-mails

## DSS/DSA

- Algoritmo de criptografia assimétrica utilizado apenas para assinatura digital
- Faz uso do SHA-1
- Não pode ser utilizado para troca de chaves ou cifragem

![[Criptografia_Assimtrica.png]]
