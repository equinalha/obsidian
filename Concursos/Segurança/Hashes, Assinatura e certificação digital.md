---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-26T18:25:00
Owner:
  - Eduardo Quinalha
---
# Definições

- Algoritmos criptográficos unidirecionais
- Resumos de tamanhos fixos, independente da entrada
- Integridade, autenticidade, não repudio e
- confidencialidade → Senhas
- Cálculos matemáticos simples, de baixo processamento
- **Utiliza o conceito de difusão**
- Avalia somente o conteúdo do arquivo.
	- Arquivos com nomes diferentes mas conteúdos indênticos vão gerar um mesmo hash

# Ataques

- **Colisão**
	- Entradas distintas, gerando o mesmo valor de hash
	- Esforço de quebra: 2^(k/2) onde k é o tamanho do digest
- **Ataque do dia do aniversário**
	- Probabilidade de duas pessoas compartilharem a mesma data de aniversário em um grupo.
	- Esse paradoxo também pode ser aplicado em contextos de criptografia, especialmente em ataques contra funções hash criptográficas.
	- O ataque baseado no Paradoxo do Aniversário em funções hash é conhecido como ataque de colisão por aniversário.
	- O objetivo é encontrar duas entradas diferentes que produzam o mesmo valor de hash.
	- O ataque de colisão por aniversário envolve a criação de um grande número de mensagens diferentes, calculando os hashes correspondentes e procurando por colisões. 
	- O método mais eficiente para encontrar uma colisão é usar a raiz quadrada do espaço de hash disponível. 
	- Se o espaço de hash for de *N* bits, a raiz quadrada de 2^N fornecerá uma estimativa do número de operações necessárias para encontrar uma colisão com alta probabilidade.
- **Falsificação existencial **
	- Refere-se a um cenário onde um atacante consegue criar uma mensagem válida e uma assinatura correspondente, sem ter acesso à chave privada do emissor. 
	- Isso significaria que a assinatura digital foi quebrada, permitindo a criação de documentos fraudulentos sem detecção. 

# Funções

- MD5
	- **HASH de 128 bits**
	- Frágil, existe possibilidade de colisões
	- **Tamanho da entrada múltiplos de 128 bits**
	- Existe uma forte probabilidade que, caso o prefixo (início) do texto seja igual, o sulfixo também será, o que facilita a busca por colisões
- SHA
	- Família de funções
	- **SHA-1 → 160 bits**
		- Bloco de 512
	- **SHA-224 → 256 truncado em 224**
	- SHA-256 → 256 bits
	- **SHA-384 → 512 truncado em 384**
	- SHA-512 → 512 bits
- SHA-3 ?

# SALT

- Mecanismo que agrega robustez
- Acrescenta-se um valor fixo de tamanho padrão, porém aleatóreo, a ser definido pelos sistemas na mensagem original

![[Hashes.png]]

# Assinatura e Certificação Digital

## Noções Gerais

- Integridade e Autenticidade (não repúdio) na troca de mensagens

## Assinatura Digital

- Criptografia Assimétrica
	- Chave privada do emissor
	- Chave pública do emissor
- Função HASH
- Processo
	- Emissor (Autenticidade e não repúdio)
		- Gera um hash do texto em claro
		- Cifra o hash com a própria chave privada
		- Envia o texto em claro com o hash cifrado
	- Receptor (Integridade)
		- Decifra o hash com a chave pública do emissor
		- Gera um novo hash do texto em claro
		- Compara os dois

![[Untitled 275.png]]

- Temporalidade
	- Temporal → Utiliza-se timestamp
	- Atemporal → Não há registro de timestamp
- Assinatura Digital - Outros conceitos (somente para o CESPE!!!)
	- Assinatura digital com criptografia Simétrica
	- Segundo o CESPE, a criptografia simétrica também garante autenticidade, portanto pode ser utilizada para assinatura digital
	- Premissa: Conhecimento mútuo da chave privada

![[Assinatura_Digital.png]]

## Certificado Digital

> [!tip] 💡
> **O certificado contém a chave pública**

- Premissas
	- Como confiar em uma chave pública divulgada?
	- A chave pública é do usuário em questão?
	- **Necessariamente envolve-se uma terceira parte confiável**
		- Autoridades certificadoras - AC (CA)
- O que é um certificado digital
	- Documento digital público
	- Contém informações de uma pessoa física, jurídiga ou um site
	- Principais informações
		- Chave pública do responsável
		- Dados do responsável
		- Dados da entidade que gerou o certificado
		- Assinaturas digitais da entidade que gerou o certificado
		- Chave pública da CA
		- Cadeia de confiança
		- Validade
	- Segue o padrão X.509
![[Untitled 276.png]]

![[Certificado_Digital.png]]

- Campos de um certificado digital:

![[Untitled 277.png]]

# ICP

- Conjunto de hardware e software, pessoal, políticas e procedimentos
- Estrutura hierárquica que permite melhor organização e gerenciamento dos certificados
- Auditoria e controle
- A autoridade raiz tem um certificado auto assinado
	- É a única que pode fazer isso
	- A garantia da autoridade raiz é a comunidade e normas regulamentadoras
- Atores e papeis
	- Autoridade certificadora (CA)
		- Responsável pela emissão dos certificados
		- Publicar os certificados para a comunidade
		- Pode ser:
			- de 1º Nível: Responsável por emitir certificados para outras AC e para a própria ICP
			- de 2º Nível: Emite certificados para usuários finais
		- **Registro, emissão e validação**
		- **Estrutura de requisição**
			- Informação de Requisição do Certificado
			- Identificador do Algoritmo de Assinatura
			- Assinatura Digital da Informação de Requisição
		- Emissão e gerenciamento da lista de certificados revogados - CRL
		- Responsável por responder às consultas de verificação de certificados gerados
		- AC Raíz
			- Relação de confiança por AC’s raízes
	- Autoridade registradora (RA)
		- Responsável pelos registros
		- **Entidade opcional, neste caso, a CA compartilha com a RA a função de registro de certificados**
		- **Não possui permissão e capacidade para emitir certificados**
		- Intermediário entre o cliente solicitante e a CA
		- Postos avançados (correios, bancos, etc…)
	- Certificados digitais
		- Documentos gerados
	- Lista de certificados revogados (CRL - Certification Revogation List)
		- Informações de apoio
		- Fator temporal (vencimento dos prazos)
		- Vulnerabilidade
		- Esquecimento sem custódia

# Protocolos de Gerenciamento

- X.509 - Versão 3 (válida para o ICP-Brasil)
- Registro
	- Usuário tornar-se conhecido antes de receber um certificado
- Inicialização
	- Instalação de materiais chaves (key materials)
	- O cliente precisa ser considerado seguro
	- Geração de chaves
	- Geração de senhas
- Certificação
	- Emissão do certificado pela CA para a chave pública do usuário
	- Armazenado em repositório público
- Recuperação do par de chaves
	- Informações base que geraram os pares de chaves para posterior recuperação em caso de perda de senha
	- **É possível recuperar o par de chaves**
- Atualização do par de chaves
	- Periódica
	- Geração de um novo par de chaves e novos certificados
- Requisição de revogação
	- Baseado em uma situação anômala
- Certificação cruzada
	- Certificação de uma CA para outra CA

# OCSP - Online Certificate Status Protocol

- Protocolo criado para resolver problemas de troca de listas de certificados revogados
- Problemas de downloads constantes das listas
- Solução: Consulta online (OCSP). Basta enviar o número de série para o servidor OCSP e obter o status do certificado
- Consolidação da consulta de todas CA’s

![[ICP.png]]

# ICP Brasil

- Controlada e gerenciada pelo Governo
- Validade jurídica
- AC’s e AR’s não se restringem a órgãos do governo
	- Entidades certificadas
		- Certsign
		- bancos
		- etc.
- Responsável pelas diretrizes: Comitê gestor da ICP Brasil

## Tipos de certificados de Assinatura Digital

> [!note] 🔥
> Resumo:

> **FUNCIONALIDADE**
> 
> **TIPO A:** Autenticação / Identificação
> 
> **TIPO S:** Sigilo / Criptografia
> 
> **TIPO T: **Hora e Data de Assinatura Digital
> 
> **ARMAZENAMENTO**
> 
> TIPO A1 / S1: **Hd / Pen drive**
> 
> TIPO A2 / S2: **Cartão Inteligente / Token**
> 
> TIPO A3 / S3: **Cartão Inteligente / Token / Nuvem**
> 
> TIPO A4 / S4: **Cartão Inteligente / Token / Nuvem**
> 
> **PRAZO DE VALIDADE**
> 
> TIPO A1 / S1: **1 ano**
> 
> TIPO A2 / S2: **até 2 anos**
> 
> TIPO A3 / S3: **até 5 anos**
> 
> TIPO A4 / S4: **até 6 anos**

- A1
	- **Geração de chaves por software**
	- **Armazenamento em harware ou repositório protegido por senha, cifrado por software**
	- **Validade de 1 ano**
	- **É um arquivo! Pode ser copiado e ser utilizado simultaneamente em vários dispositivos**
	- Frequência de publicação em LCR de 48h
	- Prazo máximo de revogação 72h
	- Não precisa de senha para o uso
- A2
	- **Geração por software**
	- **Armazenamento em cartão inteligente ou token**
	- Sem capacidade de geração de chave protegido por senha
	- Chaves mínimas de 1024 bits
	- Validade 2 anos
	- LCR: 36 e 54 h
- A3
	- **Geração e armazenamento em hardware**
	- **ou hardware aprovado pela ICP-Brasil**
	- **Validade 3 anos**
	- LCR 24/36 h
	- Precisa de senha para o uso
- A4
	- **Geração e armazenamento em hardware**
	- **ou hardware aprovado pela ICP-Brasil**
	- **Validade 3 anos**
	- **Chave mínima de 2048 bits**
	- LCR 12/18 h

## Tipos de certificados de Sigilo

Seguem as mesmas características e prazos dos certificados Ax:

- S1
- S2
- S3
- S4

## Tipos de certificados

- Pessoa física (e-CPF)
	- Mesma validade jurídica do CPF
	- Não vale para NFE
	- Declaração de IRPF
	- Serviços de justiça, RFB
- Pessoa jurídica (e-CNPJ)
	- Versão digital do CNPJ
	- IRPJ
	- Serviços da RFB
	- e-Social, FGTS, etc.
- Sistemas/Equipamentos/Aplicações

## Certificados específicos para profissionais

- Advogados
- Médicos
- Contadores

![[ICP_Brasil.png]]
