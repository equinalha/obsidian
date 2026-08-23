---

---
# 🧮 Resumo de Lógica Formal (Símbolos)

## 1. Quantificadores (Quem ou Quantos?)

Eles dizem a qual quantidade de elementos a sua regra se aplica.

- $\forall$** (Quantificador Universal):**
	- **Lê-se:** "Para todo", "Todos", "Qualquer que seja".
	- **Exemplo:** $\forall x P(x)$ (Todos são felizes).
- $\exists$** (Quantificador Existencial):**
	- **Lê-se:** "Existe", "Existe pelo menos um", "Algum".
	- **Exemplo:** $\exists x P(x)$ (Existe pelo menos um que é feliz / Alguém é feliz).
- $\nexists$** (Negação Existencial):**
	- **Lê-se:** "Não existe", "Nenhum".
	- **Exemplo:** $\nexists x P(x)$ (Não existe ninguém feliz / Nenhum é feliz).
- $\exists !$** (Existencial Único):**
	- **Lê-se:** "Existe um, e somente um", "Existe um único".
	- **Exemplo: **$\exists ! x P(x)$ (Existe apenas uma pessoa feliz).

## 2. Conectivos Lógicos (As "ligações")

Eles unem duas frases ou condições para criar uma regra maior.

- $\sim ou \neg$** (Negação):**
	- **Lê-se:** "Não", "É falso que".
	- **Exemplo:** $\neg P(x)$ (Não choveu).
- $\land$** (Conjunção):**
	- **Lê-se:** "E". *(A regra só é verdade se AMBAS as partes forem verdades).*
	- **Exemplo:** $A \land B$ (Estudei **e** passei).
- **$\lor$ (Disjunção Inclusiva):**
	- **Lê-se:** "Ou". *(A regra é verdade se UMA ou AMBAS as partes forem verdade).*
	- **Exemplo:** $A \lor B$ (Vou ao cinema **ou** vou ao parque).
- $\underline{\lor} ou \oplus$** (Disjunção Exclusiva):**
	- **Lê-se:** "Ou... ou...". *(Exatamente uma tem que ser verdade; não podem ser as duas juntas).*
	- **Exemplo: **$A \oplus B$  (**Ou** estou vivo **ou** estou morto).
- $\rightarrow$** (Condicional / Implicação):**
	- **Lê-se:** "Se... então...", "Implica que".
	- **Exemplo:** $A \rightarrow B$ (**Se** chover, **então** levo o guarda-chuva).
- $\leftrightarrow$** (Bicondicional / Equivalência):**
	- **Lê-se:** "...se, e somente se...".
	- **Exemplo:** $A \leftrightarrow B$ (Vou à praia **se, e somente se**, fizer sol).

## 🚨 Macete de Ouro para Provas: Negação de Quantificadores

As bancas de prova **adoram** pedir para você negar uma frase com "Todos" ou "Algum". A regra é simples: para negar um quantificador, você **troca o símbolo pelo seu oposto** e **nega a ação da frase**.

- **Negar o TODOS ( **$\forall$**):** Você troca por *Existe* ( $\exists$) e nega a frase.
	- *Frase:* "Todos os políticos são honestos." $(\forall x P(x))$
	- *Negação:* "Existe **pelo menos um** político que **não é** honesto." $(\exists x \neg P(x))$
	- *(Atenção: A negação de "Todos são" NUNCA é "Nenhum é". Basta UM falhar para que a regra do "Todos" seja quebrada).*
- **Negar o EXISTE/ALGUM **$(\exists)$**:** Você troca por *Todos* $(\forall)$ e nega a frase.
	- *Frase:* "Alguém gabaritou a prova." $(\exists x P(x))$
	- *Negação:* "**Todos não** gabaritaram a prova" (ou simplesmente "**Nenhum** gabaritou a prova"). $(\forall x \neg P(x))$

## Condicional (→)

- Equivale ao “se” e “então”
- Implica a ocorrência de um termo necessário (Q) mediante o termo suficiente (P)
| P | Q | P**→Q** |
| --- | --- | --- |
| V | V | V |
| V | F | F |
| F | V | V |
| F | F | V |
- Equivalências
	- **P → Q = ~P V Q**
	- **P → Q = ~Q → ~P**

## Bicondicional (↔)

- Só será falsa se as proposições tiverem valores diferentes
- **Se e somente se**
| A | B | A**↔B** |
| --- | --- | --- |
| V | V | V |
| V | F | F |
| F | V | F |
| F | F | V |
- Equivalências
	- **P↔Q ≡ (P→Q)∧(Q→P)**
	- **P↔Q ≡ (P∧Q)∨(~P∧~Q)**
	- **P↔Q ≡ ~(P⊕Q)**

## Tautologia

- É uma proposição cuja tabela verdade é sempre verdadeira
- Exemplo:
	- **p V ~p**

## Contradição

- Proposição cuja tabela verdade é sempre falso
- Exemplo
	- **p /\ ~p**

## Contingência

- Proposição cujos valores lógicos podem ser tanto V ou F
- Depende diretamente dos valores atribuídos às proposições simples que a compõem

# Lógica Argumentativa

## Conceitos

- **Premissas**
	- **Proposições que devem ser consideradas verdadeiras** para se chegar a uma conclusão
	- São hipóteses do argumento
- **Silogismo**
	- **Argumento dedutivo composto por duas premissas e uma conclusão**
- **Argumentos**
	- Dedutivos
		- Não produzem conhecimento novo
	- Categóricos
		- Apresentam proposições categóricas
	- Hipotéticos
		- Não apresentam proposições categóricas
		- Fazem uso dos conectivos

## Argumentação dedutiva

- Em um argumento** dedutivo**, a regra de inferência é de natureza lógica: é impossível que a conclusão seja falsa quando se assume que as premissas são verdadeiras.
- geral para particular
- Exemplo:
	- Todos os animais são mortais.
	- Peixe é um animal.
	- Logo, o peixe é mortal.
- **Validade**
	- Característica dos **argumentos dedutivos**
	- O argumento dedutivo é **válido** quando a **conclusão é necessariamente verdadeira** uma vez que as **premissas são CONSIDERADAS verdadeiras**
	- Um argumento dedutivo é **inválido** quando, CONSIDERADAS as **premissas como verdadeiras,** a conclusão **não é necessariamente verdadeira.**
	- Um argumento dedutivo **inválido** também é conhecido por **sofisma** ou falácia formal.
	- **Podemos ter um argumento válido nas seguintes situações:**
		- Premissas **verdadeiras** e conclusão **verdadeira**;
		- Premissas **falsas** e conclusão **verdadeira**; e
		- Premissas **falsas** e conclusão **falsa**.
		- Não é possível ter um argumento válido com **premissas verdadeiras e conclusão falsa.**
	- Método prático para validar ou invalidar um argumento
		- Supor a conclusão falsa
		- A partir de então, verificar se ainda assim, é possível ter todas as premissas verdadeiras
- **Veracidade**
	- Característica das proposições
- **Representação**
![[SubPages/Pessoal/images/image 67.png]]
	- Também pode ser representado na forma de uma condicional:
![[SubPages/Pessoal/images/image 68.png]]
- **Regras de Inferência**
	- Apresentam argumentos válidos
	- **Modus Ponens (afirmação do antecedente)**
		- **Premissa 1: **Se p, então q
		- **Premissa 2: **p
		- **Conclusão: **q
	- **Modus Tollens (negação do consequente)**
		- **Premissa 1:** Se p, então q
		- **Premissa 2:** ~q
		- **Conclusão:** ~p
	- **Silogismo Hipotético**
		- **Premissa 1:** Se p, então q
		- **Premissa 2:** Se q, então r
		- **Conclusão: **Se p, então r
	- **Dilema Construtivo:**
		- **Premissa 1: **Se p, então q
		- **Premissa 2: **Se r, então s
		- **Premissa 3: **p ou r
		- **Conclusão: **q ou s
	- **Dilema Destrutivo:**
		- **Premissa 1: **Se p, então q
		- **Premissa 2: **Se r, então s
		- **Premissa 3: **~q ou ~s
		- **Conclusão: **~p** **ou ~r

## Argumentação Indutiva

- A verdade das premissas não basta para assegurar a conclusão
- A conclusão representa uma extensão dos fatos enunciados nas premissas para um novo caso, ou para todos os casos (generalização).
- particular para o geral
- Exemplo
	- Todo gato é mortal.
	- Todo cão é mortal.
	- Todo pássaro é mortal.
	- Todo peixe é mortal.
	- Logo, todo animal é mortal.

## Argumentação Abdutiva

- A conclusão é inferida por representar a melhor explicação para os fatos enunciados nas premissas. 
- Aborda possibilidades
- Exemplo
	- Quando chove, a grama fica molhada.
	- A grama está molhada, então pode ter chovido.

## Analogia

- Num argumento por analogia defende-se que, se duas coisas são semelhantes em alguns aspetos, é provável que também sejam semelhantes noutros.
- É um argumento indutivo e nunca dedutivo, onde a conclusão está associada a uma probabilidade e não uma certeza