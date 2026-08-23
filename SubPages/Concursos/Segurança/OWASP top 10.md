---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-17T10:19:00
Owner:
  - Eduardo Quinalha
---
# Conceitos

## SLE (Single Loss Expectancy)

- Custo monetário esperado de uma única ocorrência de risco
- **perda potencial da empresa se uma ameaça específica ocorrer**
- Valor do Ativo x Fator de exposição (Exposure factor - EF) = SLE

## ALE (Annualized Loss Expectancy)

- Expectativa de perda anual
- ALE = SLE x ARO

## EF (Exposure Factor)

- Fator de exposição
- porcentagem de perda que uma ameaça ocorrida pode ter sobre certo ativo.

## ARO (Annualized Rate of Occurrence)

- Estimativa da frequência com que um risco específico irá ocorrer em um período anualizado
- pode variar entre 0,00 (nunca), 1,0 (ao menos uma vez ao ano) até valores maiores do que 1 (várias vezes ao ano) ou qualquer outro valor.

# Práticas de programação segura e revisão de código

[Desatualizado](https://owasp.org/www-pdf-archive/OWASP_SCP_Quick_Reference_Guide_v2.pdf)

- Validação e Sanitização de Input
	- Remover dados potencialmente nocivos ou maliciosos
- Tratamento de erros
	- Um tratamento inadequado pode trazer problemas de segurança, especialmente em relação a vazamento de dados
	- Pode-se criar um tipo customizado e genérico de erros, que irá substituir as mensagens de erro padrão.
- Logging

# Tipos de Ataque a Aplicações Web

## XSS

- **Tipos:**
	- **Cross-site scripting armazenado (XSS Persistente)**
		- XSS Armazenado, também conhecido como XSS Persistente, é considerado o tipo de ataque XSS mais prejudicial. O XSS Armazenado ocorre quando a entrada fornecida pelo usuário é armazenada e, em seguida, processada em uma página da Web. Os pontos de entrada típicos para XSS Armazenado incluem fóruns de mensagens, comentários em blogs, perfis de usuário e campos de nome de usuário. Um invasor normalmente explora essa vulnerabilidade injetando cargas de XSS em páginas populares de um site ou passando um link para uma vítima, induzindo-a a visualizar a página que contém a carga de XSS armazenada. A vítima visita a página e a carga útil é executada no lado do cliente pelo navegador da vítima.
	- **Cross-site scripting Refletido (XSS Não persistente)**
		- O tipo mais comum de XSS é conhecido como XSS Refletido (também conhecido como XSS Não persistente). Nesse caso, a carga útil do invasor deve fazer parte da solicitação enviada ao servidor da Web. Em seguida, é refletido de volta de maneira que a resposta HTTP inclua a carga útil da solicitação HTTP. Os invasores usam links maliciosos, e-mails de e outras técnicas de para induzir a vítima a fazer uma solicitação ao servidor. A carga útil XSS refletida é então executada no navegador do usuário.
		- O XSS Refletido não é um ataque persistente, portanto, o invasor precisa entregar a carga útil a cada vítima. Esses ataques costumam ser feitos por meio de redes sociais.
	- **Cross-site scripting baseado em DOM**
		- XSS baseado em DOM refere-se a uma vulnerabilidade de cross-site scripting que aparece no DOM (Document Object Model) em vez de parte do HTML. Em ataques de cross-site scripting refletidos e armazenados, você pode ver a carga útil da vulnerabilidade na página de resposta, mas no cross-site scripting baseado em DOM, o código-fonte HTML do ataque e a resposta serão os mesmos, ou seja, a carga útil não pode ser encontrada na resposta. Ele só pode ser observado em tempo de execução ou investigando o DOM da página.
		- Um ataque XSS baseado em DOM é geralmente um ataque do lado do cliente, e a carga maliciosa nunca é enviada ao servidor. Isso torna ainda mais difícil a detecção de WAFs (Web Application Firewalls) e engenheiros de segurança que analisam os logs do servidor porque nunca veem o ataque. Os objetos DOM que são manipulados com mais frequência incluem o URL (document.URL), a parte âncora do URL (location.hash) e o Referrer (document.referrer).

## CSRF

- É necessário que o usuário já esteja autenticado no site legítimo
- No site malicioso, haverá um link para o site legítimo, efetuando uma operação qualquer, por exemplo, troca de e-mail do cadastro
- Este link se aproveita do fato de que o usuário já estava logado naquela aplicação
- Como resultado, o atacante pode ganhar controle da conta do usuário no site legítimo (que pode ser uma rede social, ou banco, por exemplo)

![[Untitled 269.png]]

![[Untitled 270.png]]

- Condições necessárias para o ataque:
	- Deve ser possível realizar uma ação relevante na aplicação via chamada de API em segundo plano (sem necessidade de interação com o usuário)
	- Controle de sessão baseado em cookies
	- Os parâmetros da chamada da API devem ser previsíveis
		- Ou seja, a necessidade de um parâmetro que não seja previsível de fora da aplicação (ex: CSRF Token), quebra o ataque
	- O usuário deve estar autenticado na aplicação alvo
- Deixou a lista do OWASP Top 10, pois é facilmente bloqueado pela aplicação

## Sequestro de Sessão

- O atacante consegue obter um identificador de sessão de outro usuário logado na aplicação
	- Normalmente obtido com o uso de outros ataques
- Com o uso de um proxy especial, ele substitui em todas as chamadas à aplicação, seu ID pelo ID da vítima, podendo executar ações em seu nome
- Por exemplo: substituição de cookie de sessão

## Fixação de Sessão

- Funciona ao contrário do sequestro de sessão.
- Neste caso, o atacante é que especifica o ID de sessão que a vítima vai usar
- Depende de outras técnicas como cross-site scripting, manipulação de tráfego de rede e cross-site cooking
- A ideia é induzir a vítima a se logar no site com um ID de sessão especificado
- Depois de autenticado, como o atacante conhece o ID e sessão, poderá navegar como se fosse a vítima

![[Untitled 271.png]]

## Clickjacking

- Utilizando `iframe` o atacante cria uma página de isca que é colocada em cima (z-index) da aplicação desejada
- O usuário é induzido a clicar em áreas da página falsa que correspondam aos comandos da página verdadeira
- Na prática o usuário estará clicando em algum comando da página alvo que poderá revelar o ID de sessão da vítima

## Spidering

Os Spiders são amplamente usados pelos mecanismos de pesquisa da web para indexar todas as páginas de um site, seguindo os links de uma página a outra. O motor de busca resume o conteúdo e adiciona os links aos seus índices.

## Fuzzing

- técnica utilizada para testar erros em aplicações
- capacidade de detectar defeitos que usuários não descobrem com facilidade.
- consiste, basicamente, em enviar entradas randômicas para a aplicação
- também é conhecida como injeção de falhas, teste de validação robusta, teste de sintaxe ou teste de negação.
- Como exemplo, podemos citar um formulário que foi criado com a expectativa de receber determinado conjunto de caracteres e dados, como informações de telefone, CEP, entre outros.
- Assim, o Fuzzing injetará informações incomuns como tamanhos diferenciados, caracteres não utilizados e, paralelamente, monitorará o comportamento da aplicação, pois esta poderá travar ou vazar dados de forma indevida.

# OWASP Top 10 2021

> [!note] 🔥
> **Quebrou a Criptografia, Injetou Insegurança na Configuração, Compôs Autênticos Dados de Monitoramento do Servidor**

## 1 - Quebra de Controle de Acesso

> [!tip] 💡
> Vulnerabilidades que possibilitam burlar os controles de acesso

- Controle de acesso visa estabelecer limites para as ações de um determinado usuário
- Falhas neste controle podem levar a divulgação, modificação ou destruição de informações
- **Vulnerabilidades comuns (causas)**
	- Violação do princípio de privilégio mínimo
	- Ignorar as verificações de controle manipulando diretamente a URL ou chamadas de API
	- Elevação de privilégio
	- Manipulação de metadados, como adulterar token ou cookie
	- Configuração incorreta de CORS, permitindo acesso à API de origens não autorizadas/seguras
	- Forçar a navegação para páginas autenticadas como usuário não autenticado
- **Como prevenir**
	- Controle só é confiável no **lado do servidor**, ou de forma que o usuário não tenha acesso
	- Usar filosofia do** privilégio mínimo** (negar por padrão)
	- **Desativar listagem de diretórios no servidor**
	- Identificadores de sessão devem ser invalidados após o logout
	- **Tokens JWT sem estado devem ter vida curta**
	- Seguir os padrões OAuth para revogação de acesso
	- Limite de taxa de acesso à API (Evitar ataques automatizados)
	- **Reutilizar os mecanismos de controle de acesso.**

## 2 - Falhas criptográficas

> [!tip] 💡
> Vulnerabilidades relacionadas à criptografia e falta dela

- Falhas relacionadas ao uso de criptografia ou à falta dela
- **Causas**
	- Tráfego sem criptografia
	- Algoritmo fraco ou antigo
	- Chaves reutilizadas
	- Senhas usadas como chave
- **Prevenção**
	- Classificar os dados usando automatismo
	- Não armazenadas dados confidenciais desnecessariamente
	- Criptografar dados confidenciais armazenados
	- **Desativar armazenamento em cache para respostas que contenham dados confidenciais**
	- Armazenar senhas usando **SALT** e funções de hash adaptáveis, com fator de atraso
	- Usar criptografia autenticada em vez de somente criptografia
		- Garante também a autenticidade além da confidencialidade provida por criptografia comum

## 3 - Injeção

> [!tip] 💡
> Vulnerabilidades relacionadas à possibilidade de injeção de códigos na aplicação

- Pode ser XSS, SQL Injection e Controle externo do nome do arquivo ou caminho
- **Causas**
	- Dados fornecidos pelo usuário não validados ou limpos
	- Chamadas não parametrizadas, sem escape, usadas diretamente no interpretador
		- **Nota:** Mesmo quando parametrizados, os procedimentos armazenados ainda podem introduzir injeção de SQL se PL/SQL ou T-SQL concatenar consultas e dados ou executar dados hostis com EXECUTE IMMEDIATE ou exec().
	- Uso de concatenação com dado fornecido externamente para uso em chamadas ou procedimentos
- **Tipos de injeção mais comuns**
	- SQL, NoSQL
	- Comando OS
	- ORM, LDAP
	- EL (Expression Language)
- A revisão do código fonte é o melhor método de detecção de vulnerabilidade do tipo Injection
- **Prevenção**
	- incluir ferramentas de teste de segurança de aplicações estáticos (**SAST**), dinâmicos (**DAST**) e interativos (**IAST**) no pipeline de CI/CD
	- Usar ORM
	- Usar “safelist” no lado do servidor
	- Consultas dinâmicas residuais, escape de caracteres especiais.
	- **Use LIMIT e outros SQL de controle em consultas para evitar a divulgação em massa de registros no caso de injeção de SQL.**

## 4 - Design Inseguro (Introduzido em 2021)

> [!tip] 💡
> Vulnerabilidades decorrentes da forma como a aplicação foi construída: tratamento de erros, arquitetura, armazenamento, etc.

- Abordagem que vai além do Shift Left, colocando a SI em etapas anteriores ao design
- ***Geração de Mensagem de Erro Contendo Informações Confidenciais*****,**
- *Armazenamento Desprotegido de Credenciais*,
- *Violação de Limites de Confiança* 
- *Credenciais Insuficientemente Protegidas*.
- **Possui foco na pré codificação, isto é, antes do código ser desenvolvido**
- **Prevenção**
	- Utilizar um [ciclo de vida de desenvolvimento seguro](/ced56d423ca64ab68af50c0c22380512)
	- Usar bibliotecas de padrão de projeto seguros
	- Usar modelagem de ameaças
	- Separar os tenants de maneira robusta
	- Limitar o consumo de recursos por usuário ou serviço

## 5 - Configuração Incorreta de Segurança

> [!tip] 💡
> Vulnerabilidades causadas por utilização de senhas padrão, bibliotecas vulneráveis, etc.

- Falta de proteção apropriada em qualquer parte da stack ou permissões incorretas em serviços de nuvem
- Recursos desnecessários ativados ou instalados
- Contas padrão e senhas ainda ativadas e inalteradas
- Falta de tratamento de erros que revela o stack trace da aplicação
- Software desatualizado ou vulnerável
- **Prevenção**
	- Plataforma mínima sem recursos desnecessários
	- Ambientes de desenvolvimento, qualidade e produção configurados de forma idêntica e automatizada
	- Gerenciamento de vulnerabilidades (aplicação de patches)
	- Arquitetura segmentada
	- Envio de diretivas de segurança para clientes (security headers)

## 6 - Componentes Vulneráveis e Desatualizados

> [!tip] 💡
> Uso de recursos vulneráveis e/ou desatualizados

- Desconhecimento das versões dos componentes utilizados, inclusive dependências aninhadas
- Software vulnerável, sem suporte ou desatualizado
- **Prevenção**
	- Remover dependências não utilizadas
	- Monitorar CVE’s. Ter um inventário com as versões utilizadas. Automatizar este processo
	- Utilizar componentes apenas de fontes oficiais

## 7 - Falhas de Identificação e Autenticação

> [!tip] 💡
> Falta de controles rígidos relacionados a autenticação

- A aplicação permite preenchimento automatizado (robôs) baseado em lista de credenciais
- Permite força bruta
- Senhas padrão e fracas
- Recuperação de credenciais fraca
- Armazenamento de dados e senhas em texto simples, criptografadas ou com hash fracos
- MFA ausente ou ineficaz
- Reutiliza do ID de sessão
- Não invalida ID de sessão
- **Prevenção**
	- MFA
	- Não permitir credenciais padrão
	- Verificação de força de senha
	- Retardar tentativas repetidas de login com falha
	- Usar gerenciador de sessão do lado do servidor que gere ID de sessão aleatória com alta entropia
		- Não usar este ID em URL
		- Invalidado após logout

## 8 - Falhas de Software e Integridade de Dados (Introduzido em 2021)

> [!tip] 💡
> Falta de controle da integridade dos componentes

- Código e infra que não protegem contra violação de integridade
- Dependência de plugins ou bibliotecas não confiáveis
- Atualização automática de software com pouco controle de integridade e autenticidade
	- O atacante pode ter comprometido o repositório e colocado uma versão comprometida de software
- **Prevenção**
	- Assinaturas digitais para verificar a fonte dos dados
	- Utilizar repositórios confiáveis
	- Ferramenta automatizada de verificação de segurança nas bibliotecas

## 9 - Falhas de Registro e Monitoramento de Segurança

> [!tip] 💡
> Falhas de monitoramento e logs

- Falta de log de eventos auditáveis como logins falhos, transações, …
- Mensagens de erro inadequadas ou confusas
- Falta de monitoramento de atividades suspeitas
- Logs armazenados apenas localmente
- Limiares de alerta não configurados ou ineficazes
- **Prevenção**
	- Logar falhas de login
	- Logs gerados em formato facilmente consumível por ferramentas de gerenciamento
	- Transações de alto valor com trilha de auditoria e controle de integridade
	- Estabelecer plano de resposta e recuperação de incidentes

## 10 - Falsificação de Solicitação do Lado do Servidor (SSRF) (Introduzido em 2021)

> [!tip] 💡
> Uso de URL fornecidas pelo usuário sem o devido tratamento

- Ocorrem quando a aplicação sempre busca um recurso externo sem validar a URL informada pelo usuário.
- **Prevenção**
	- Segmentar o acesso a recursos remotos em rede separada
	- Políticas de firewall negar por padrão
	- Higienizar os dados de entrada
	- Utilizar lista positiva
	- Não enviar a resposta crua ao cliente
	- Desabilitar redirecionamento HTTP

# OWASP SAMM

[https://drive.google.com/file/d/1cI3Qzfrly_X89z7StLWI5p_Jfqs0-OZv/view](https://drive.google.com/file/d/1cI3Qzfrly_X89z7StLWI5p_Jfqs0-OZv/view)

- Software Assurance Maturity Model
