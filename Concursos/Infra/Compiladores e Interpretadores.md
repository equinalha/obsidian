---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-08-30T10:09:00
Owner:
  - Eduardo Quinalha
---
# Compiladores

![[Untitled 517.png]]

- Programas capazes de traduzir o código fonte para linguagem de mais baixo nível:
	- Linguagem de montagem
	- Código-objeto
		- Versão compilada e montada de um código fonte
		- Não é diretamente executável
		- Possui tabelas de símbolos, constantes, strings e outras referências
- **Pré-processador**
	- Efetua conversões léxicas no código fonte (texto puro)
	- Interpreta diretivas direcionadas ao compilador como #include e #define
	- Exclui comentários
	- Nem toda linguagem usa pré-processador
- **Compilador**
	- O processo de compilação é dividido em duas fases:
		- **Análise ou Front-End**
			- Análise léxica (Scanner)
			- Sintática (Parser)
			- Semântica
			- Geração de código intermediário
		- **Síntese ou Back-End**
			- Otimização
			- Geração do código final

## Análise léxica

- Trabalho feito pelo analisador léxico ou **scanner**
- Divide o código em símbolos léxicos chamados **tokens**
- Os tokens são guardados em uma tabela de símbolos
- Os espaços em branco e comentários são removidos

## Análise sintática

- Parsing
- Coloca os tokens em uma estrutura hierárquica, como uma **árvore**
- Analisa a sequência lógica dos tokens
- Um erro sintático resulta de uma sequência de tokens mal formulada
- Não se preocupa com os valores e operandos

## Análise semântica

- Erros semânticos = Erros de sentido
	- Refere-se ao sentido daquilo que está sendo comunicado
- Checagem de tipos
- Fluxos de controle
- Unicidade de declaração de variáveis
- **Erros semânticos podem ser detectados durante a compilação e durante a execução**
- Usa a árvore de análise sintática como entrada

## Geração de código intermediário

- Transformação da árvore da análise sintática em uma linguagem intermediária, mais próxima do código objeto do que do código fonte
- Ainda permite manipulação

## Otimização

- Examina-se o código objeto em busca de padrões e substitui-os por códigos mais eficientes
- Pode ser dependente ou independente
	- **Independente**: Aplicada antes da geração do código assembly, também conhecida como **Análise de Fluxo**
	- **Dependente**: Otimização aplicada no código assembly gerado
- **Blocos básicos ou “Trecho de código em linha reta”:**  
	- Trechos de código executados em sequencia, sem instruções de desvio condicional ou de repetição
	- Podem ser otimizados de 3 formas:
		- Na representação intermediária, antes da geração do código
		- Durante a geração do código, fazendo com que seja gerado já de forma intermediária
		- Após a geração, diretamente no código objeto

## Geração do código final

- Gera-se o código de montagem, necessário para a próxima fase (**montagem**)

## Montador (assembler)

- Converte o código em linguagem de montagem em um equivalente em linguagem de máquina
- **Cross-assembler:** Quando a execução se dará em um processador diferente do que está fazendo a montagem
- **Macro-assembler:** Usa macro para expansão do código, cada vez que uma macro for encontrada
- **Micro-assembler:** permite a escrita de micro-instruções (processadores micro-programáveis)

## Linker

- Recebe como entrada um conjunto de arquivos-objeto, bibliotecas, arquivos de controle, parâmetros, etc. e junta tudo num **módulo de carga **que pode posteriormente ser carregado na memória.

## Loader

- Recebe o módulo de carga e transferem seu código para a memória.
- Existem dois tipos
	- **Carregadores binários ou absolutos**
		- mais simples
		- apenas copiam o arquivo para a memória
		- o executável é simplesmente uma imagem binária do programa em execução
		- Necessitam ser carregados sempre para o mesmo local da memória para executarem corretamente
		- arquivos **.com**
	- **Realocáveis**
		- Pode ser alocado em qualquer local da memória para execução
		- Usa endereçamento relativo
		- **.exe**

## Bibliotecas

- **Estáticas**
	- São carregadas para dentro do binário final
	- É tratado como se fizesse parte do código
	- O executável final ocupa mais espaço na memória
- **Dinâmicas (compartilhadas)**
	- são apenas referenciadas no executável final
	- Se a biblioteca for atualizada, o executável já poderá usufruir da atualização
	- Pode ser utilizada por mais de um programa, otimizando a ocupação de memória
	- Existe uma latência de carregamento da biblioteca, deixando o programa final mais lento
	- DLL do windows, LIB do linux