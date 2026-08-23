---
base: "[[Simulados.base]]"
Desempenho: 0.91
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-10-25
---
58 - Conforme a WCAG, o princípio denominado perceptível determina que os componentes de interface devem ser compreensíveis para o usuário. 

> Errado

> - **Perceptível**
>     - O conteúdo deve ser apresentado de maneira que os usuários possam **percebê-lo com seus sentidos**, especialmente visão e audição.
>     - Exemplo de diretrizes: fornecer alternativas textuais para imagens, criar legendas para conteúdos audiovisuais, adaptar a apresentação de conteúdo visual para facilitar a percepção.
> - **Operável**
>     - A interface e os componentes de navegação devem ser **utilizáveis por todos os usuários**, incluindo aqueles que **não usam um mouse** ou têm **dificuldades motoras**.
>     - Exemplo de diretrizes: permitir a **navegação por teclado**, **evitar elementos piscantes** que possam causar crises epilépticas e oferecer **tempos razoáveis** para completar tarefas.
> - **Compreensível**
>     - O conteúdo e a interface devem ser apresentados de forma que os usuários possam **entender o texto** e como navegar e interagir.
>     - Exemplo de diretrizes: criar uma estrutura clara, **facilitar a leitura** e compreensão do conteúdo e **evitar elementos de navegação confusos** ou inconsistentes.
> - **Robusto**
>     - O conteúdo deve ser **compatível com tecnologias de assistência** e ser interpretado de maneira confiável em uma ampla variedade de dispositivos, incluindo navegadores e leitores de tela.
>     - Exemplo de diretrizes: usar código HTML/CSS limpo e sem erros, compatível com as tecnologias assistivas, e garantir que o conteúdo continue acessível à medida que novas tecnologias surgem.

60 - As diretrizes da WCAG determinam que deve ser mantido o contexto da aplicação quando um componente diferente recebe o foco do usuário. 

> Certo

Alterações de contexto são permitidas apenas quando solicitadas pelo usuário.** Previsível**

83 - O uso extensivo de pseudoelementos no CSS3 pode melhorar a estrutura semântica de um documento HTML. 

> Errado

> - Usar pseudoelementos para adicionar ícones ou decorações não vai mudar o entendimento semântico do conteúdo pelos buscadores ou leitores de tela.
> - Os pseudoelementos não criam novos elementos no DOM; eles apenas permitem estilizar partes de elementos existentes.
> - Já o uso correto de tags semânticas (como <section>, <nav> ) melhora a estrutura semântica.
> 
> 
> Pseudoelementos no CSS3 são palavras-chave que permitem definir estilos para partes específicas de um elemento, sem a necessidade de adicionar classes ou IDs adicionais no HTML. Eles são usados para selecionar e estilizar elementos virtuais, ou partes de um elemento, que não são representados diretamente no DOM. Os pseudoelementos mais comuns são:
> 
> 1. `**::before**`: Insere conteúdo antes do conteúdo real de um elemento. Ele é frequentemente usado para adicionar ícones ou outros elementos decorativos
> 2. `**::after**`: Insere conteúdo após o conteúdo real de um elemento. Assim como `::before`, pode ser usado para adicionar elementos decorativos.
> 3. `**::first-line**`: Aplica estilos à primeira linha de um bloco de texto. Isso é útil para dar destaque ou formatar a introdução de um parágrafo.
> 4. `**::first-letter**`: Aplica estilos à primeira letra de um bloco de texto, permitindo efeitos visuais, como letras capitais ou decorativas.
> 
> ```plain text
> p::first-letter {
>     font-size: 2em;
>     float: left;
>     margin-right: 0.1em;
> }
> ```
