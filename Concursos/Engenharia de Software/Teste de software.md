---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:02:00
Owner:
  - Eduardo Quinalha
---
# Definições

- Engano → Defeito → Erro → Falha
	- **Defeito**: deficiência mecânica ou algorítmica que, se ativada, pode levar a uma falha Instrução ou comando incorreto 
	- **Erro**: item de informação ou estado de execução inconsistente. Desvio em relação ao que era esperado
	- **Falha**: evento notável em que o sistema viola suas especificações.
- Um **engano** introduz um **defeito** no software
- O **defeito**, quando ativado, pode produzir um **erro**
- O **erro**, se propagado até a saída do software, constitui uma **falha**.

![[Untitled 643.png]]

# Objetivos

- Lógica interna (caixa branca)
- Entradas e saídas (caixa preta)
- Encontrar erros
- **Não garante um software livre de erros**
- Testes devem ser **rastreáveis aos requisitos de cliente**
- Devem ser planejados
- Aplica-se o princípio de pareto

# Abordagens

![[Untitled 644.png]]

- **Funcional (caixa preta)**
	- Focada nas entradas/saídas especificadas em **requisitos funcionais**
	- Baseado em pré e pós condições
	- Utilizado nas etapas posteriores
	- Principais técnicas
		- **Grafos**
		- **Matriz ortogonal**
		- **Particionamento de equivalências**
			- Particiona o domínio de entrada em classes de maior significância
			- Estas classes são equivalentes
			- Por exemplo, se o domínio de entrada são números inteiros, pode-se dividir entre positivos e negativos e utilizar uma pequena amostra de cada partição
		- **Análise de valores limítrofes**
			- Estatisticamente, os erros concentram-se nos limites das entradas válidas
			- Esta técnica trabalha junto com o particionamento
			- Testa-se os valores que estão nas bordas dos valores aceitáveis (limite)
- **Estrutural (caixa branca)**
	- Focado nas estruturas internas
	- Os caminhos internos são conhecidos
	- Os testes são elaborados com o intuito de testar todos os caminhos internos
	- Testar todas as estruturas de dados internas
	- Principais técnicas
		- Testes de caminhos
		- Testes de estruturas de controle
		- Testes de complexidade ciclomática
			- Métrica que fornece uma medida quantitativa da complexidade lógica
			- Denota o número de caminhos possíveis dentro de um módulo
			- Dá ideia de um limite superior necessário
![[Untitled 645.png]]

- **Mista (caixa cinza)**
	- Algum conhecimento sobre as estruturas

# Estágios

- Testes são agrupados de acordo com o momento ou nível de especificidade

![[Untitled 646.png]]

## 1. Teste unitário

- Primeiro nível (camada) de testes
- Feito pelo próprio desenvolvedor
- Menor granularidade possível
- Em geral é um teste de **Caixa branca, ****mas também pode ser utilizada a abordagem de caixa preta**
- Baby Steps
	- Buscar pela solução mais simples
	- Não pela modificação mais simples

## 2. Testes de integração

- Segundo nível (camada) de testes
- Testa a interação dos componentes do software
- Está relacionado com a arquitetura do software
- Testa as interfaces entre os módulos
- Integração Top-Down
- Integração Botton-Up
- Integração gradual

![[Untitled 647.png]]

- Integração** **<u>**primeiro-em-profundidade**</u>**(depth-first)** integra **todos os componentes em um caminho de controle principal da estrutura do programa**.
- Já a integração <u>**primeiro-em-largura**</u>** (breadth-first)** incorpora **todos os componentes diretamente subordinados a cada nível, movendo-se através da estrutura horizontalmente**.

## 3. Teste de Aceitação / Validação

- Terceira camada
- Focado nos fluxos de negócio
- Procura demonstrar a conformidade com os requisitos
- Deve ser o mais próximo possível do ambiente real
- 3.1. **Testes Alfa**
	- Visa testar/entender como o usuário irá utilizar o sistema
	- Conduzido pelo cliente, porém **nas instalações do desenvolvedor**
	- **Acontece em ambiente controlado**
- 3.2. **Testes Beta**
	- Testes em ambiente real (do cliente)
	- O desenvolvedor não está presente (geralmente)
	- **Acontece em ambiente real**
	- Segue um roteiro fornecido pelo desenvolvedor

## 4. Testes de Sistema

- Testes que envolvem o conjunto completo: Software, Hardware, Processos, Informações, Outros sistemas, etc.
- Último nível de testes
- Ambiente completo e integrado

# Tipos de Testes

## **Teste de Regressão**

- Cada vez que é adicionado ou alterado algo no software
- Surgem novas entradas e saídas
- A lógica muda
- Os testes de regressão visam reexecutar os testes que foram executados anteriormente, de forma a garantir que a alteração não tenha inserido algum comportamento indesejado
- São desenvolvidos de modo incremental durante o desenvolvimento do software, para avaliar se alterações no código introduziram comportamentos inesperados

## **Teste de Fumaça**

- Visa testar **funcionalidades básicas**
- Executado após a integração de software
- Analogia à engenharia hidráulica, onde injeta-se fumaça na tubulação a fim de localizar vazamentos

## **Teste de Recuperação**

- Força o sistema a falhar
- Observa-se como ele se comporta após retornar ao funcionamento, recuperando-se da falha
- A recuperação pode ser automática ou manual

## **Teste de Segurança**

- PenTesting
- SQL Injection, XSS, etc…
- **DAST, SAST e IAST**
	- Localizar vulnerabilidades de software
	- Dentro do conceito de DevSecOps
	- **SAST **(Static Application Security Testing)
		- Varredura do código fonte
		- Caixa branca
	- **DAST **(Dynamic Application Security Testing)
		- Feito com o aplicativo em execução
		- Pentesting
		- Caixa preta
		- Leva o ambiente em consideração
	- **IAST** (Interactive Application Security Testing)
		- Na prática, combina SAST e DAST no processo

## **Teste de Carga (estresse)**

- Forçar o sistema em situações de alta demanda
- Tem caráter destrutivo
- Até quando ele aguenta?
- Memória, I/O, Disco

## **Testes de Desempenho**

- Tempo de resposta
- Requisitos não funcionais

## **Teste de Usabilidade**

- Ponto de vista do usuário
- Fatores subjetivos
- UX/UI
- Testar o quão amigável é o sistema

# Mock Objects

- Objetos simuladores utilizados em teste de software
- Imitam o comportamento de um objeto real, de forma controlada
- É possível determinar comportamentos a fim de permitir realizar os testes de acordo com os cenários específicos
- Podem simular um serviço e testar interações complexas
- Exemplo
	- Deseja-se testar uma função de envio de uma notificação por e-mail.
	- Ao invés de depender de um serviço de envio de e-mails real, pode-se utilizar mock para simular o evnio

# Stubs

- Similar aos mocks objects, porém mais simples
- **stub possui um comportamento previsível de retorno**
- Usamos o **mock** quando queremos **saber se uma função vai ser chamada corretamente**, quantas vezes ela vai ser chamada, se os parâmetros esperados são os corretos
- já o **stub** vai nos dizer se o resultado do código retorna de acordo com os parâmetros passado, se retorna sucesso, erro ou exceção por exemplo, é previsível.

# Automação de Testes

- Testes Unitários
- Conjunto Integrado
- Geradores de dados
- Analisadores dinâmicos
- Ferramentas
	- **JUnit**
		- Testes funcionais unitários
		- Pode ser usado para testes de regressão e integração
		- Testes automatizados, rápidos e programáveis
		- Annotations
			- `@Test`
			- `@Assert`
			- `@EnabledOnOs` a classe de teste anotado ou método de teste está **habilitado apenas em um ou mais sistemas operacionais especificados**
			- `@EnabledOnJre`  **ativado apenas em uma ou mais versões especificadas do JRE**
			- `@DisabledIfSystemProperty`**desativado se o valor da propriedade do sistema especificada corresponder à expressão regular especificada**
			- `@DisabledIfEnvironmentVariable `**ativado se o valor da variável de ambiente responder à expressão regular encontrado**
			- `@EnabledIf `**utilizada  para condicionar a ativação da classe de teste anotado ou método de teste pela avaliação de um script. **Por *default*, o JUnit **fornece suporte para avaliação de scripts JavaScript**
		- Integrado à IDE
		- Pode-se modularizar os testes
	- **Selenium**
		- Aplicações web
		- Selenium Web Driver
			- Driver específico para cada navegador
		- Selenium Grid
			- Processamento distribuído
	- **JMeter**
		- Testes de carga, estresse e desempenho
		- Teste dinâmico
		- Possui interface gráfica para acompanhamento
		- Pode simular um grupo de usuários enviando requisições simultâneas

# Debugging

- Etapa que pode suceder os testes
- Visa corrigir os erros encontrados nas fases de teste
- Abordagens
	- Força bruta: Prints espalhados pelo código para sinalizar o caminho
	- Backtracking: Segue o stack tracing
	- Eliminação de causa: Formula-se uma hipótese e os dados favoráveis a ela são colocados na entrada

# Clean Code / Clean Test

- direciona a escrita de um código simples, direto e inteligível, que transmita clareza e seja de fácil compreensão.
- segue 5 regras do acrônimo **FIRST** (*fast, independent, repeatable, self-validating, timely*)
	- 1. **Rapidez**: a execução dos testes deve ser rápida. Caso a execução seja lenta, os testes serão executados com pouca frequência e os problemas não serão identificados cedo o bastante para serem consertados de forma fácil 
	- 2. **Independência**: os testes devem ser **independentes um dos outros**, pois caso sejam dependentes a falha de um causará a falha de outro 
	- 3**. Repetitividade**: os testes devem poder ser repetidos em **qualquer ambiente** (produção, teste, qualquer notebook e etc.) 
	- 4. **Auto validação**: os testes **devem ter uma saída booleana: passou ou não passou**, a fim de evitar ter que comparar arquivos ou fazer análises para identificar se foi bem sucedido ou não 
	- 5.** Pontualidade**: devem-se “criar os testes de unidade imediatamente antes do código de produção no qual serão aplicados", ou seja, deve-se **testar antes de colocar o sistema em ambiente de produção.**

![[Teste_de_Software.png]]

![[nse-4244678879652699523-temp.jpg.jpg]]

# Complexidade Ciclomática

- Mede a complexidade baseado no grafo do controle de fluxo
- Determina a quantidade de caminhos independentes pelo código fonte
- Tem influência em teste de software
- Cálculo $V(G) = E - N + 2P$ onde:
	- $E$ é o número de arestas no grafo
	- $N$ é o número de nós no grafo
	- $P$ é o número de componentes conectados do grafo (para programas com apenas um componente, P é 1).
- Outra forma é através do número de regiões, onde $V(G) = R + 1$ onde $R$ é o número de regiões fechadas por um ciclo.
- Exemplo:
![[Untitled 648.png]]
	- Nós: 8
	- Arestas: 9
	- V(G) = 9 - 8 + 2 = 3
	- Calculando pelo número de regiões fechadas:
	- V(G) = 2 + 1 = 3

### Passos para Calcular a Complexidade Ciclomática

1. **Desenhe o Grafo de Controle de Fluxo**: 
	1. Crie um grafo que representa o fluxo de controle do programa. 
	2. Cada nó representa um bloco de código ou uma instrução, e cada aresta representa a transferência de controle de um bloco para outro.
2. **Conte os Nós (N) e Arestas (E)**: 
	3. Conte o número total de nós e arestas no grafo.
3. **Aplique a Fórmula**: 
	4. Use a fórmula $V(G) = E − N + 2P$ para calcular a complexidade ciclomática.
