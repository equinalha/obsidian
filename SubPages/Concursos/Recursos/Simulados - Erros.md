---
base: "[[Recursos.base]]"
cover: "[[Simulados - Erros.jpeg]]"
Tags:
  - Recursos
---
> [!note]+ # TCE-RJ 2021
> ## To Do
> 
> - [ ] Classificação de risco p/ Top10 x Owasp risk Rating
> - [ ] Spidering
> - [x] CSRF vs Relação de confiança site navegador
> - [x] Controle de inferência em SGBD
> - [x] Tomcat 10
> - [ ] DFD
> - [x] Atributos NULL em tabelas dimensão
> - [x] Revisar ETL
> - [x] Plano de execução: Quais informações fornece? Inclui o uso de índices
> - [x] Índices - Quais cláusulas são afetadas, cardinalidade
> - [x] Big Data - Tipos de análises
> - [x] Uso da cláusula HAVING
> 
> ---
> 
> > [!tip] 💡
> > Julgue o item a seguir, quanto às ferramentas e técnicas de exploração de vulnerabilidades em aplicativos *web*, à *Open Web Application Security Project* (OWASP) e às ameaças e vulnerabilidades em aplicações *web.*
> > O tipo de ataque em que o atacante explora a **relação de confiança que um sítio possui com o navegador** que o acessa é conhecido como CSRF (*cross-site request forgery*). 
> 
> R: Certo
> 
> Uma das condições necessárias para o sucesso do ataque CSRF é que a vítima esteja logada no site que o atacante deseja explorar em nome deste. Além disso, faz-se necessário que o 
> controle de sessão deste site seja feito por meio de cookies. Assim, o atacante inclui em um site diverso uma chamada de API, via iframe ou até mesmo via um link malicioso, que faz 
> uma chamada de API sem o conhecimento do usuário, porém se aproveitando de que o cookie de sessão é enviado automaticamente pelo navegador.
> 
> Ou seja, a relação de confiança mencionada é exatamente esta sessão salva no navegador do usuário.
> 
> > [!tip] 💡
> > Entre os fatores de *design* em COBIT 2019, o cenário de ameaças identifica o tipo de risco relacionado à informação e à tecnologia ao qual a empresa está atualmente exposta e indica quais áreas de risco estão excedendo os riscos típicos da organização.
> 
> R: Errado
> 
> > [!tip] 💡
> > No Tomcat 10, os arquivos de definição e de configuração, incluindo o arquivo server.xml, localizam-se por padrão no diretório /bin. 
> 
> R: Errado
> 
> These are some of the key tomcat directories:
> 
> /**bin **- Startup, shutdown, and other scripts. The *.sh files (for Unix systems) are functional duplicates of the *.bat files (for Windows systems). Since the Win32 command-line 
> lacks certain functionality, there are some additional files in here.
> /**conf **- Configuration files and related DTDs. The most important file in here is **server.xml**. It is the main configuration file for the container.
> /**logs **- Log files are here by default.
> /**webapps **- This is where your webapps go.
> 
> > [!tip] 💡
> > No padrão Gigabit Ethernet, tanto no modo de operação *half-duplex *quanto no modo *full-duplex,* o uso do protocolo CSMA/CD para evitar colisões é dispensável, em razão da extensão de portadora, uma característica voltada à prevenção de colisões incluída originalmente nas definições do padrão. 
> 
> R: Errado
> 
> No Full duplex, uma vez que os canais são exclusivos tanto para TX quanto para RX, não há a necessidade de detecção de colisão pois esta é impossível de acontecer.
> No entanto, em half duplex, como há o compartilhamento do canal, é necessário um algoritmo de detecção de recuperação em caso de colisão
> 
> No padrão IEEE 802.3 AE (10Gb Ethernet) é que foi removido o CSMA/CD pois este não prevê o uso em half-duplex
> 
> > [!tip] 💡
> > No modelo IaaS de serviço em nuvem, o consumidor gerencia e controla sistemas operacionais, armazenamento, componentes e sistemas de segurança e a infraestrutura de nuvem subjacente.
> 
> E: Errado
> O erro está em "infraestrutura de nuvem subjacente", uma vez que isto é responsabilidade do provedor de nuvem.
> 
> > [!tip] 💡
> > Para a aplicação em questão, caso se utilize a análise de pontos de função (APF), o tamanho de pontos de função sem fator de ajuste será 48.
> > ![[Untitled 850.png]]
> 
> R: Certo
> Lembrando dos valores:
> 
> <!-- Column 1 -->
> |   | ALI | AIE |
> | --- | --- | --- |
> | Baixa | 7 | 5 |
> | Média | 10 | 7 |
> | Alta | 15 | 10 |
> 
> <!-- Column 2 -->
> |   | EE | SE | CE |
> | --- | --- | --- | --- |
> | Baixa | 3 | 4 | 3 |
> | Média | 4 | 5 | 4 |
> | Alta | 6 | 7 | 6 |
> 
> > [!tip] 💡
> > A arquitetura MVC (*Model-View-Controller*) separa a interface do usuário da funcionalidade e do conteúdo de informações; a camada *model *contém todo o conteúdo e a lógica de processamento específicos à aplicação bem como acesso a fontes de dados e toda a funcionalidade de processamento específica para a aplicação. 
> 
> R: Certo
> A camada model é responsável não só pelos dados como também seus acessos e regras de negócio. Ela é responsável por manter o estado do sistema. A camada controller apenas trata das requisições e envia comandos tanto para a camada view como para a controller também.
> 
> > [!tip] 💡
> > No RUP, a disciplina Requisitos tem como fulcro definir uma interface de usuário para o sistema, possuindo, como uma de suas tarefas, desenvolver a visão geral para o sistema; 
> a disciplina Teste valida o sistema quanto aos requisitos elicitados.
> 
> R: Certo
> 
> Estão entre as atividades da disciplina de Requisitos:
> 
> Identificar os agentes que interagem com o sistema, desenvolver os casos de uso, definir as fronteiras do sistema, definir uma base para planejamento do conteúdo técnico das iterações, definir uma base para estimar custo e tempo e **definir uma interface de usuário para o sistema.**
> 
> A disciplina de **Teste**, por sua vez, tem como objetivos localizar e documentar defeitos na qualidade, validar as funções do software e **verificar se os requisitos foram implementados de forma adequada.**
> 
> 
> > [!tip] 💡
> > A análise estática de código-fonte adota a verificação por boas práticas, que considera elementos como edentação e convenção de nomes.
> 
> R: Errada
> 
> Não apenas isso.
> 
> **Verificação por estilo:** Considera elementos como identação, espaços e tabs, convenção de nomes, número de parâmetros, alinhamento na vertical, formato e presença de comentários, dentre outros. São todos os aspectos que contribuem para tornar o código mais padronizado, organizado e legível. A ferramenta mais utilizada para verificação por estilo é o Checkstyle;
> 
> 
> **Verificação por boas práticas:** Aplica uma gama de regras para verificar se práticas corretas estão sendo realizadas, como evitar duplicação de código, garantir o correto uso de encoding, implementação do método clone(), tamanho de métodos e classes, tamanho de parâmetros, uso do padrão Singleton, criação desnecessária de variáveis locais e muitas outras. O conjunto de regras é extenso e visa garantir que o código apresente as melhores práticas possíveis. A ferramenta de verificação mais utilizada para aplicar boas práticas é o PMD;
> 
> **Verificação por bugs: **Trata de encontrar erros no sistema. Isto é importante para antecipar a identificação de problemas no software (até antes mesmo de sua execução pelo cliente). A ferramenta mais utilizada para identificação de bugs é o Firebug.
> 
> > [!tip] 💡
> > O *failover* em um sistema de banco de dados, sem nenhum prejuízo para a qualidade das informações consultadas, é garantido pela replicação das bases de dados em sítios distintos.
> 
> R: Errado
> 
> Embora a replicação em sítios distintos seja uma estratégia possível de failover, a qualidade não pode ser garantida de forma absoluta.
> 
> - Replicação síncrona e assíncrona podem ter comportamentos diferentes em caso de falhas.
> - Possíveis inconsistências de dados devido à latência na replicação de dados entre sítios geograficamente distribuídos.
> - A falha durante o processo de replicação pode resultar na perda de algumas transações, o que afetaria a qualidade das informações.
> 
> > [!tip] 💡
> > No processo de análise de desempenho de um banco de dados, na análise de** planos de execução** é possível diagnosticar que a exclusão de índices pode levar à melhoria de desempenho do banco de dados.
> 
> R: Correto
> 
> Planos de execução mostram quando um índice está ou não sendo utilizado. Se um índice for pouco utilizado ou nem mesmo utilizado em consultas, pode ser benéfico excluí-lo, uma vez que em operações de escrita e atualização estes representam um custo adicional ao SGBD.
> 
> > [!tip] 💡
> > No processo de otimização de consultas de bancos de dados relacionais, em consultas que façam uso de ORDER_BY, a criação de índice nas colunas ORDER_BY é uma opção que pode melhorar o desempenho de tais consultas.
> 
> R: Correto
> 
> Em consultas que requerem uma ordenação específica dos resultados, o uso de índices nas colunas de ordenação pode melhorar o desempenho. Os índices ordenados permitem que o banco de dados recupere e retorne os resultados na ordem desejada sem a necessidade de uma etapa adicional de ordenação.
> 
> > [!tip] 💡
> > A análise prescritiva é empregada na análise de Big Data para relatar acontecimentos e para fazer previsões de comportamentos futuros de indivíduos e processos.
> 
> R: Errado
> 
> A análise prescritiva é utilizada para fornecer recomendações, o que fazer caso um cenário se concretize. O relato de acontecimentos (O que aconteceu) é fornecido pela análise descritiva. Já previsões de comportamentos futuros pode ser fornecido pela análise preditiva.
> 
> > [!tip] 💡
> > Em um banco de dados relacional, foram criadas as seguintes relações, posteriormente transformadas e preenchidos seus dados em tabelas. As chaves primárias estão realçadas em itálico.
> 
> ```sql
> professor (cpf_professor, nome, titulação, salario)
> curso (cod_curso, titulo, objetivo, cpf_professor_coord)
> contrato (cpf_professor, cod_curso, data_inicio)
> ```
> 
> Tendo como referência as informações precedentes, julgue o item subsecutivo.
> 
> O comando SQL a seguir cria uma visão com todos os dados dos professores e dos respectivos cursos que eles coordenam, não incluindo os cursos sem um professor com a função de coordenador.
> 
> ```sql
> create view coordenador_curso as
> select * from professor p left outer join curso s on true
> where p.cpf_professor = s.cpf_professor_coord;
> ```
> 
> R: Correto
> 
> `LEFT OUTER JOIN` = `LEFT JOIN`
> 
> Tendo isso em mente, a junção será feita de forma que serão exibidas todos os registros da tabela professor com sua respectiva correspondência na tabela curso, inclusive professores que não tenham nenhuma correspondência na tabela curso (`NULL`), pois a condição posta na cláusula `JOIN` é simplesmente `TRUE` (sempre/Todas as ocorrências).
> 
> No entanto, na cláusula `WHERE` está sendo feita a filtragem, restringindo apenas àquelas ocorrências em que `cpf_professor = cpf_professor_coord`