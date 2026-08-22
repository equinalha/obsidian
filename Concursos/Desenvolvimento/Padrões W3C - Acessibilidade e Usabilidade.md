---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-25T09:31:00
Owner:
  - Eduardo Quinalha
---
# W3C e WCAG

- O W3C (World Wide Web Consortium) é uma **organização internacional que cria padrões para a Web**
- a missão do W3C é desenvolver protocolos e diretrizes que garantam que a Web cresça de maneira padronizada, segura e acessível. 
- Esses padrões incluem recomendações para HTML, CSS, XML, entre outras tecnologias essenciais para o funcionamento da Web.
- WCAG (Web Content Accessibility Guidelines), por sua vez, é um **conjunto de diretrizes desenvolvidas pelo W3C** que tem como foco a acessibilidade na Web. 
- As WCAG têm como objetivo orientar desenvolvedores e designers na criação de conteúdo web acessível a pessoas com deficiência. 
- As WCAG estão divididas em três níveis de conformidade:
	- **Nível A**: o mínimo essencial para tornar o conteúdo acessível;
	- **Nível AA**: um nível de acessibilidade que atende a grande parte das necessidades de acessibilidade;
	- **Nível AAA**: o nível mais alto, que proporciona a máxima acessibilidade.
- Para cada diretriz são definidos **critérios de sucesso testáveis**

# Organização

- É dividido em princípios e diretrizes

## Princípios: **PORCo**

![[Concursos/images/Untitled 91.png]]

- **Perceptível**
	- O conteúdo deve ser apresentado de maneira que os usuários possam **percebê-lo com seus sentidos**, especialmente visão e audição.
	- Exemplo de diretrizes: fornecer alternativas textuais para imagens, criar legendas para conteúdos audiovisuais, adaptar a apresentação de conteúdo visual para facilitar a percepção.
- **Operável**
	- A interface e os componentes de navegação devem ser **utilizáveis por todos os usuários**, incluindo aqueles que **não usam um mouse** ou têm **dificuldades motoras**.
	- Exemplo de diretrizes: permitir a **navegação por teclado**, **evitar elementos piscantes** que possam causar crises epilépticas e oferecer **tempos razoáveis** para completar tarefas.
- **Compreensível**
	- O conteúdo e a interface devem ser apresentados de forma que os usuários possam **entender o texto** e como navegar e interagir.
	- Exemplo de diretrizes: criar uma estrutura clara, **facilitar a leitura** e compreensão do conteúdo e **evitar elementos de navegação confusos** ou inconsistentes.
- **Robusto**
	- O conteúdo deve ser **compatível com tecnologias de assistência** e ser interpretado de maneira confiável em uma ampla variedade de dispositivos, incluindo navegadores e leitores de tela.
	- Exemplo de diretrizes: usar código HTML/CSS limpo e sem erros, compatível com as tecnologias assistivas, e garantir que o conteúdo continue acessível à medida que novas tecnologias surgem.

## Diretrizes

- Estão abaixo dos princípios
- Total de 13
- Objetivos básicos a serem atingidos pelos autores
- As diretrizes **não são testáveis**

## Critérios de sucesso

- Para cada diretriz
- Testáveis

## Técnicas

- Para cada diretriz e critério de sucesso
- Podem ser:
	- Necessárias
	- Sugeridas
- Todas estas camadas de orientação (princípios, diretrizes, critérios de sucesso e técnicas de tipo necessária e de tipo sugerida) funcionam em conjunto para fornecer orientações sobre como tornar o conteúdo mais acessível.

# Princípio 1: Perceptível

- As informações e os componentes da interface do usuário devem ser apresentados em formas que possam ser percebidas pelo usuário.

## Diretrizes

### 1.1 Alternativas em Texto

- fornecer alternativas textuais para qualquer conteúdo não textual
- Todo o conteúdo não textual que é exibido ao usuário tem uma alternativa textual que serve a um propósito equivalente, exceto para as situações indicadas abaixo.
	- **Controle ou Entrada de Dados: **Neste caso deve possuir um nome que descreve sua finalidade
	- **Mídia com base no tempo: **Neste caso deve ser fornecido, no mínimo, uma identificação descritiva do conteúdo
	- **Teste ou exercício: **Teste ou exercício que ficaria inválido caso fosse apresentado em texto. Neste caso deve ser fornecido uma identificação descritiva do conteúdo
	- **Experiência sensorial:** Fornecer identificação descritiva do conteúdo
	- **CAPTCHA:** Deve ser descrito a finalidade. Usar formas alternativas com diferentes modos de saída
	- **Decoração, formatação:** Deve ser implementado de forma que possa ser ignorado por tecnologias assistivas

### 1.2 Mídias com base em tempo

- Devem ser disponibilizados mídias alternativas
- Legendas, audiodescrição, interpretação em língua de sinais

### 1.3 Adaptável

- As instruções fornecidas para compreender e utilizar o conteúdo não dependem somente das características sensoriais dos componentes
- O sequenciamento lógico das ideias pode ser feito via programação (semântica html)

### 1.4 Discernível

- Facilitar a audição e a visualização de conteúdo aos usuários, incluindo a separação entre o primeiro plano e o plano de fundo.

# Princípio 2: Operável

- Os componentes de interface de usuário e a navegação devem ser operáveis.

## Diretrizes

### Acessível por Teclado

- Fazer com que as funcionalidades fiquem disponíveis a partir de um teclado
- Caso o mecanismo de foco do teclado seja diferente dos usuais (Tab, setas) o usuário deverá ser informado
- Não pode ser requerido temporização para a digitação

### Tempo Suficiente

- Fornecer aos usuários tempo suficiente para ler e utilizar o conteúdo
- Deve ser possível permitir a prolongação do tempo para 10x com uma ação simples
- Exceções
	- Tempo real: Por exemplo leilões
	- Essencial: Ao prolongar o tempo invalidaria a atividade
	- 20 horas: limite superior a 20 horas

### Convulsões e Reações Físicas

- Não criar conteúdo de uma forma conhecida por causar convulsões e reações físicas.
- Piscar, flash, em 3 Hz

### Navegável

- Fornecer maneiras de ajudar os usuários a navegar, localizar conteúdos e determinar onde se encontram.
- ignorar blocos de conteúdo que são repetidos em várias páginas web.

### Modalidades de Entrada

- Torna mais fácil para os usuários operar a funcionalidade por meio de várias entradas além do teclado.

# Princípio 3: Compreensível

- A informação e a operação da interface de usuário devem ser compreensíveis.

## Diretrizes

### Legível

- Tornar o conteúdo do texto legível e compreensível.
- Idioma definido (ou inferido) via programação
- Nível de leitura (ensino fundamental)
- Formas de identificar significado de siglas, jargões, expressões e termos técnicos
- Mecanismos de identificação de pronúncia

### Previsível

- Fazer com que as páginas web apareçam e funcionem de modo previsível.
- Seguir padrões em múltiplas páginas web
- Alterações de contexto iniciadas apenas a pedido do usuário

### Assistência de Entrada

- Ajudar os usuários a evitar e corrigir erros.
- Rótulos de entrada
- Destacar erros imediatamente detectados
- Ajuda contextual

# Princípio 4: Robusto

- O conteúdo deve ser robusto o suficiente para poder ser interpretado de forma confiável por uma ampla variedade de agentes de usuário, incluindo tecnologias assistivas.

## Diretrizes

### Compatível

- Maximizar a compatibilidade entre os atuais e futuros agentes de usuário, incluindo tecnologias assistivas.