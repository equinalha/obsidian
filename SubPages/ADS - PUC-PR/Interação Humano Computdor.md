---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-08-15T20:25:00
Status: Not started
Description: ""
---
# Tipos de interfaces

- Física
	- Botões
	- Caixa de entrada
- Perceptiva
	- Mensagens de alerta
	- sons
- Conceitual
	- Quando conseguimos concluir uma atividade por meio da entrada e saída do dispositivo

# ATP

> [!tip] 💡
> App de comida tipo caixa surpresa: 
> - A pessoa preenche o perfil com suas preferências e restrições alimentares
> - O preço é padronizado por categoria, por exemplo (econômico, regular e prêmium)
> - O usuário poderá escolher por tipo, por exemplo: Lanche, almoço, café da tarde ou sobremesas
> - A pessoa recebe uma caixa com a comida (lanche, refeição, etc.) escolhido “aleatoriamente” pelo aplicativo
> - Os fornecedores são lojas, lanchonetes ou restaurantes cadastrados, dentro de um raio máximo de distância do usuário que serão sorteados para atender o pedido
> - O restaurante é escolhido de acordo com alguns critérios: Estar dentro do raio máximo de atendimento, ter cardápio compatível com as preferências e tipo escolhido pelo usuário
> - O restaurante poderá enviar dentro da embalagem um folder com sua apresentação, cardápio, vouchers, mensagens e brindes
> - O aplicativo vai otimizar a distribuição de pedidos entre os restaurantes cadastrados, de forma mais equalitaria possível, para que todos tenham oportunidade de atender um cliente
> 
> Possíveis personas:
> 
> - Usuário
> - Estabelecimento credenciado
> - Entregador

Você faz parte de um programa de trainee em uma organização de software. Esta organização tem como objetivo crescer no mercado (nacional e internacional). A diretoria desta organização decidiu promover um desafio da melhor ideia para lançamento de um novo produto de software. Então, decidiu fazer uma reunião com todos os membros da área de TI e explicar as necessidades da organização, deixando claro que não existe restrição com relação a ideia do produto. No entando, é priomordial que a interface do usuário seja fácil de usar.  Para isto, qualquer membro da organização pode enviar ao setor de TI ideias de projetos para serem avaliadas. As 10 melhores ideias serão selecionadas para concorrer ao desafio. Você saiu super motivado desta reunião, porque é uma oportunidade de ser efetivado na organização, e enviou uma proposta para ao gerente do setor de TI. Três semanas depois você vê em sua caixa de correio a resposta que seu projeto, com a seguinte mensagem:

Bom dia,

Parabéns!

Seu projeto foi selecionado para participar do desafio para desenvolver um novo produto de software para organização. Para participar deste desafio você deve apresentar três entregas:

- Na primeira entrega, você deve apresentar o contexto de uso do Usuário e a Especificação dos cenários de uso;
- Na segunda, você deve apresentar protótipos de um produto de software inovador, considerando às necessidades do Usuário; e,
- Na última entrega, os resultados da avaliação heurística do protótipo desenvolvido. Atenciosamente, Gerente da TI.

![[SubPages/ADS - PUC-PR/images/Untitled 15.png]]

## **EXEMPLO**

Exemplo de Pixar storytelling

Era uma vez uma moça chamada Romilda. TODOS OS DIAS, Romilda  saía de casa 1 hora antes da entrada na faculdade, pois tinha medo de perder o ônibus e se atrasar, porque os horários das linhas disponíveis no site não eram cumpridos.

UM CERTO DIA, ela descobriu um aplicativo de celular que mostra um mapa em tempo real da localização das linhas de ônibus selecionadas e a estimativa de chegada ao destino, utilizando informações de localização dos próprios usuários de transporte coletivo. POR CAUSA DISSO, Romilda pôde planejar com confiabilidade a hora de chegada na parada de ônibus, sem correr o risco de perdê-lo ou ficar esperando em dias frios ou chuvosos de Curitiba.

POR CAUSA DISSO, Romilda tem mais tempo para realizar atividades físicas, rotinas e tarefas antes de sair de casa para ir a faculdade, sem se preocupar em perder seu ônibus e chegar atrasada em sua faculdade ou qualquer outro lugar. ATÉ QUE FINALMENTE Romilda conseguiu, com o tempo extra, estudar inglês em casa, o que lhe gerou uma promoção no trabalho.

![[SubPages/ADS - PUC-PR/images/Untitled 16.png|Perfil de Usuário]]

## Persona

Persona é uma personagem fictícia, arquétipo hipotético de um grupo de usuários reais, criada para descrever um usuário típico (COOPER, 1999). Em *design* de projetos interativos, é utilizada para descobrir, modelar e refinar as necessidades de um grupo de usuários. Portanto, tem os seguintes objetivos: gerar consenso no time, entender as dores e olhar o problema sob a óptica do usuário.

1. **Identidade:** dê nome, inclua uma foto e inclua os dados demográficos do perfil do usuário (sexo, idade etc.).
2. **Objetivos:** quais são os objetivos desta persona?
3. **Habilidades:** quais são as habilidades desta persona (educação, treinamento e competências específicas)?
4. **Tarefas****:** quais tarefas básicas ou críticas a persona realiza?
5. **Relacionamentos:** entender com quem a persona se relaciona ajuda a identificar outros *stakeholders.*
6. **Requisitos****:** quais são as necessidades?
7. **Expectativas****:** como ela acredita que o produto funciona?

![[SubPages/ADS - PUC-PR/images/Untitled 17.png]]

Em resumo, como criar uma persona?

- Coletar os dados dos diferentes usuários.
- Realizar perguntas a usuários.
- Analisar os dados coletados.
- Estruturar a persona.
- Compartilhar a persona com a equipe.

## Estória do usuário

## **EXEMPLO**

**Formato da estória do usuário**

Como <papel ou persona>, eu deveria ser capaz de solicitar um <requisito>, a fim de adquirir um <benefício>, ou seja, um serviço/uma funcionalidade do sistema.

**Descrição de estória**

Como **gerente do financeiro**, eu quero **poder consultar o saldo de todas as vendas** para poder tomar uma decisão sobre o negócio.

**Critérios de aceitação**

- Entrar com seu usuário.
- Selecionar o tipo de relatório.
- Entrar com o período ou mês no qual deseja fazer a pesquisa.
- O sistema deve apresentar o relatório em formato PDF para o usuário.

## Mapa de estória do usuário

![[SubPages/ADS - PUC-PR/images/Untitled 18.png]]

![[SubPages/Concursos/images/Untitled 19.png]]

![[SubPages/Concursos/images/Untitled 20.png]]

# 12 princípios de design

![[SubPages/Concursos/images/Untitled 21.png]]

- Visibilidade
	- Manter as funções visíveis ou pelo menos facilitar a localização do controle apropriado para a tarefa com agilidade
	- Quanto mais visíveis estiverem as funções, mais facilmente os usuários saberão como proceder
- Consistência
	- Operações similares, com elementos similares
	- Tornam as interfaces fáceis de utilizar e aprender
	- Resultados de inconsistência
		- Dificuldade para lembrar procedimentos
		- Grandes chances de acontecerem erros
		- Frustração na troca de versão
- Navegação
	- Auxiliar o usuário a se movimentar pelo sistema
	- Mapas, sinais orientadores
- Controle
	- Permitir que o usuário tenha o controle na realização de uma tarefa
	- Cancelar ou dar continuidade em uma tarefa
- Feedback
	- Retornar ao usuário a informação do que foi executado
	- Retorno constante e consistente intensifica a sensação de controle

# Storyboard

São elementos de um *storyboard*:

- cenário;
- pessoas envolvidas;
- ambiente;
- tarefa a ser cumprida;
- sequência.

Para seu desenvolvimento, pergunte-se:

- Quais são os passos envolvidos?
- O que faz com que uma pessoa use o artefato?
- Que tarefa está sendo ilustrada?

![[SubPages/Concursos/images/Untitled 22.png]]

![[SubPages/Concursos/images/Untitled 23.png]]

# Avaliação

## Categorias

- ambiente controlado;
	- experimentos, observação, entrevistas, questionários
	- a equipe de *design* pode controlar o que o usuário vai fazer.
	- pode ser medida a quantidade de erros cometidos pelo usuário para realizar uma tarefa ou quanto tempo ele leva para tal.
	- Esses experimentos podem ser registrados por meio de vídeos, registros de *log,* questionários de satisfação, observação direta do usuário realizando a tarefa e outros.
- ambiente natural;
	- pouco ou nenhum controle sobre as atividades dos participantes.
	- captura automática diretamente da aplicação.
- qualquer ambiente não envolvendo o usuário.
	- **métodos de inspeção** são usados para prever o comportamento do usuário nos contextos em que o sistema será usado e nos tipos de atividade que os usuários realizam.
		- avaliação heurística (avaliação com uso de princípios de usabilidade), 
		- percursos cognitivos (simular resolução de problema de usuário) e 
		- *analytics* (*web analytics*).
