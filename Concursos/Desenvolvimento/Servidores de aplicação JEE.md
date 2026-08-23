---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-10-01T17:19:00
Owner:
  - Eduardo Quinalha
---
# Revisão de conceitos

## 4 camadas JEE

- Cliente
- Web
- Negócio
- Dados

## APIs

- JDBC
	- Envio de instruções para BD
	- Drivers
- JPA
	- ORM
	- POJOS
	- JPQL
- JTA
	- Transações
- JNDI
	- Diretório
	- Serviço de nomes
	- Semelhante ao DNS
- JMS
	- Mensageria
	- JMS Provider
	- JMS Clients
	- Administered Objects
	- Comunicação assíoncrona
	- Fracamente acoplado
- Servlets
	- Conteúdo web dinâmico
	- Tratamento de requisições HTTP
- EJB
	- Lógica de negócio
	- Componente do tipo servidor que executa no container do servidor de aplicação
	- Abstrai questões de infraestrutura, segurança, disponibilidade e escalabilidade
![[Untitled 548.png]]
	- Fornece recursos para o desenvolvimento de aplicações java baseado em componentes distribuídos, transacionais, seguros e portáveis
- JSP
	- Extensão da tecnologia servlet
	- Enquanto o foco do EJB é negócio, o foco do JSP é a camada de apresentação
![[Untitled 549.png]]


# Container JEE

Container fornece uma interface entre um componente e as funcionalidades de baixo nível específicas da plataforma.

## 5 containers J2EE

1. J2EE Server → É o mais completo, fornece os containeres Servlet e EJB
2. Container EJB → Gerencia a execução dos Enterprise Beans (modelos de negócio)
3. Container Web → JSP e Servlet
4. Application client container → gerencia a execução dos componentes da aplicação cliente. Roda no cliente
5. Servlet container → JSP e Servlet

# Servidores de aplicação JEE

- Implementam toda a especificação JEE
- Também chamado full compliance
- Implementam web container e EJB container
- Facilidades providas:
	- Gerenciamento de servidor
	- Gerenciamento de transações
	- Gerenciamento de segurança
	- Tolerância a falhas
	- Balanceamento de carga
	- Failover
	- Mensageria
	- Pool de recursos

# JBOSS / Wildfly

- Código aberto (até o JBOSS)
- Implementado totalmente em Java
- Roda em qualquer SO que suporte Java
- **middleware de padrão aberto**
- **JBoss Application Server (AS)**
	- Open source
	- Desenvolvida por comunidades Jboss/RedHat
	- Evolui mais rápido
	- não possui suporte oficial
	- Passou a se chamar **Wildfly**
- **JBoss Enterprise Application Platform (EAP)**
	- Versão paga
	- Evolui a partir das versões estáveis do AS
	- Possui suporte oficial
	- Troca do container que era **JBossWeb **para **Undertow**

## **Modos**

- **Standalone**
	- Iniciado pelo script JBOSS_HOME/standalone.sh ou JBOSS_HOME/standalone.bat
	- Cada instância do JBOSS atende a uma única aplicação
	- Para rodar múltiplas instâncias neste modo, cada aplicação deve ter uma pasta do JBOSS exclusiva para si
- **Domain**
	- Permite gerenciar um conjunto de instâncias do Wildfly
	- Compartilham configurações em comum
	- O gerenciamento é coordenado pelo Domain Controller
![[Untitled 550.png]]
	- **Domain Controller**
		- É o ponto central de administração em um ambiente de domínio do JBoss/WildFly. 
		- Gerencia e coordena a configuração de todos os servidores de aplicação dentro do domínio.
		- Mantém a configuração centralizada do domínio, que inclui as configurações dos servidores, perfis, subsistemas e implantações.
		- Comunica-se com os **Host Controllers**, que são responsáveis por gerenciar grupos de servidores dentro do domínio.
		- Distribui deployments nos servidores
		- Monitora o status e a saúde dos servidores no domínio.
		- **Domain Controller** não controla diretamente uma instância de servidor de aplicação no JBoss/WildFly. 
		- O controle de instâncias de servidores é feito através dos **Host Controllers**.
	- **Host Controller**
		- Responsável por gerenciar os servidores de aplicação que estão executando no mesmo host físico ou virtual. 
		- Ele inicia, para e configura esses servidores de acordo com as instruções recebidas do Domain Controller.
		- Recebe os deployments de aplicações do Domain Controller e os distribui para os servidores locais que gerencia.
		- Gerencia o ciclo de vida das instâncias locais
	- **Instâncias**
		- São as instâncias reais de JBoss/WildFly que executam as aplicações.
		- Cada instância de servidor é controlada por um Host Controller, que aplica as configurações e faz a gestão das mesmas.

## **Perfis**

Além do modo, é necessário estabelecer também um perfil de execução, que na prática implica em definir quais subsistemas serão utilizados pela aplicação.

- **default / Web**
	- Permite o uso do container web (Java EE Web)
- **full**
	- Permite o uso de toda a especificação Java EE / Jakarta EE
- **ha / Web com HA**
	- Permite o uso do perfil Java EE Web com características de HA
- **full-ha**
	- Permite o uso do perfil Java EE Full com características de HA

## **Deploy**

- Formatos WAR, JAR e EAR
- Via console web ou CLI

## **Console**

- [http://x.x.x.x:9990/console/](http://x.x.x.x:9990/console/)
- O console de administração do Wildfly é uma interface baseada na *web *que permite gerenciar o servidor Wildfly e os aplicativos implantados;
- O arquivo de configuração de segurança geralmente se chama `mgmt-users.properties`, e as credenciais de administração são armazenadas nesse arquivo. 

## **Alguns diretórios importantes:**

- welcome-content/: diretório de uso interno do servidor que não deve ser modificado por usuários finais, possui páginas de boas vindas e páginas de erros;
- **Datasources**
	- *datasource ***XA** = Transações distribuídas em várias bases de dados, e podem introduzir overhead.
	- *datasource ***non-XA** = Não usa transação e utiliza apenas um banco de dados.

## **Instalação**

- No Windows, as permissões das pastas não são configuradas automaticamente
	- Exige ação manual do administrador do sistema ou do profissional responsável pela instalação.

# Tomcat

- Características
	- Apenas uma instância é permitida por JVM, porém múltiplas instâncias podem existir em uma mesma máquina física, rodando em processos java separados, em portas separadas
	- Implementa somente o container web (servlet container)
	- Oferece tecnologias de apoio como:
		- Realms
		- Segurança
		- JNDI
		- JDBC
	- Pode atuar como servidor web HTTP
	- Pode funcionar integrado a servidores web dedicados como Apache ou IIS
	- Desmembrando:
		- Catalina - Servlet Container
		- Coyote - HTTP connector
		- Jasper - JSP Engine
- Diretórios
	- /bin
	- /conf
		- Arquivos de configuração (XML) e os DTD’s respectivos
		- o mais importante é o server.xml
		- web.xml
			- Existe um web.xml global, localizado na pasta /conf e um por aplicação, localizado na pasta /WEB-INF da aplicação
	- /logs
	- /webapps
	- 
- Recursos:
	- SSI - Server Side Includes
		- Diretivas avaliadas pelo servidor, que permitem a inclusão de conteúdo gerado dinamicamente em arquivos html existentes, tudo pelo lado do servidor
	- Possui um pequeno banco de dados embarcado, chamado **Realm**, utilizado para armazenamento de usuários e senha para a administração do servidor
	- Também pode ser utilizado via JDBCRealm: uma implementação de um Tomcat 3.X Realm que usa um conjunto de tabelas configuráveis dentro de um RDMS para armazenar os dados do usuário, essas tabelas são acessadas por meio de drivers JDBC padrão.
- Algumas configurações:

```xml
<!-- frequência das verificações por modificações nas páginas JSP para 30 segundos. -->

<init-param>
	<param-name>checkInterval</param-name>
	<param-value>30</param-value>
</init-param>

<!-- Auto Deploy: Faz a verificação periódica de arquivos .war e executa o deploy. Caso esteja false, o deploy deverá ser feito manualmente
via manager ou JMX Beans -->
<Host name="localhost"  appBase="webapps"
            unpackWARs="true" autoDeploy="true">
```

- RBAC no Tomcat

```xml
<!-- Definindo roles e restrições -->
<security-role>
    <role-name>manager</role-name>
</security-role>
<security-constraint>
    <web-resource-collection>
        <web-resource-name>management pages</web-resource-name>
        <url-pattern>/secure/*</url-pattern>
        <url-pattern>/mixed/secure3.jsp</url-pattern>
    </web-resource-collection>
    <auth-constraint>
        <role-name>manager</role-name>
    </auth-constraint>
</security-constraint>

<!-- Definindo um método de autenticação -->
<!-- Basic -->
<login-config>
    <auth-method>BASIC</auth-method>
</login-config>

<!-- Form Based -->
<!-- No tipo de autenticação form based, toda vez que o usuário tentar acessar um recurso protegido, sem estar autenticado, o Tomcat irá automaticamente redirecioná-lo para o formulário
de login -->
<login-config>
  <auth-method>FORM</auth-method>
  <form-login-config>
    <form-login-page>/login/login.jsp</form-login-page>
    <form-error-page>/login/loginfail.jsp</form-error-page>
  </form-login-config>
</login-config>

<!-- Form Based com SSL/TLS: Adicionar a configuração abaixo -->
<user-data-constraint>
  <description>Needs SSL</description>
  <transport-guarantee>CONFIDENTIAL</transport-guarantee>
</user-data-constraint>
```

- Configurando acesso ao **manager**
	- Por padrão, o Tomcat não vai permitir acesso ao manager, pois nenhum usuário configurado no arquivo `tomcat-users.xml` está associado à alguma role `manager-xxx`
	- Para habilitar acesso às interfaces de gerenciamento, é necessário criar um usuário e atribuir uma das seguintes roles:
		- **manager-gui** — Access to the HTML interface.
		- **manager-status** — Access to the "Server Status" page only.
		- **manager-script** — Access to the tools-friendly plain text interface that is described in this document, and to the "Server Status" page.
		- **manager-jmx** — Access to JMX proxy interface and to the "Server Status" page.
- **Segurança**
	- É importante saber que o Tomcat, assim como outros servidores de aplicação, utiliza um modelo de segurança que permite definir políticas para o acesso a recursos do sistema. Estas políticas são configuradas por meio de arquivos de política que detalham quais permissões são concedidas a cada parte do código que é executada no servidor.
	- As permissões em questão podem ser, de fato, tanto padrão (definidas pelo próprio sistema ou framework) quanto customizadas (criadas especificamente para atender às necessidades de uma determinada aplicação web). Isso permite que os desenvolvedores e administradores de sistemas tenham um controle granular sobre o que o código executado pode ou não fazer, melhorando a postura de segurança da aplicação.

# Clusterização

O conceito de clusterização em servidores de aplicação Java EE / Jakarta EE refere-se à capacidade de distribuir uma aplicação Java EE em vários servidores, conhecidos como nós, para melhorar a escalabilidade, disponibilidade e confiabilidade da aplicação. Um cluster é uma coleção de nós de servidor que trabalham juntos para fornecer serviços de aplicação de forma cooperativa. Aqui está como funciona a clusterização em servidores de aplicação Java EE / Jakarta EE:

6. **Configuração do Cluster**: Para começar, você precisa configurar os servidores de aplicação para funcionar em um ambiente de cluster. Isso geralmente envolve a configuração de um gerenciador de cluster que coordena a comunicação e a distribuição de tarefas entre os nós do cluster. Cada servidor no cluster deve ter acesso a um armazenamento compartilhado (como um sistema de arquivos compartilhado ou um banco de dados) para manter informações de configuração compartilhadas, como sessões de usuários e configurações de aplicativos.
7. **Balanceamento de Carga**: Um dos principais benefícios de um cluster é a capacidade de distribuir o tráfego de entrada entre os nós de forma equilibrada. Isso é feito usando um balanceador de carga que encaminha as solicitações dos clientes para os diferentes nós do cluster. O balanceador de carga pode ser um componente separado ou incorporado em alguns servidores de aplicação.
8. **Compartilhamento de Sessões**: Quando um usuário faz login em uma aplicação Java EE, uma sessão é criada para rastrear seu estado. Em um ambiente de cluster, é importante que essas sessões sejam compartilhadas entre os nós, para que, se um nó falhar, o usuário possa continuar a interagir com a aplicação em outro nó sem perder seu estado. Isso é geralmente feito usando técnicas como replicação de sessão, onde as informações da sessão são copiadas ou sincronizadas entre os nós do cluster.
9. **Distribuição de Tarefas**: Além do compartilhamento de sessões, a clusterização também pode envolver a distribuição de tarefas específicas entre os nós do cluster. Por exemplo, uma fila de mensagens pode ser distribuída entre os nós para que eles processem tarefas em paralelo.
10. **Alta Disponibilidade**: A clusterização é fundamental para fornecer alta disponibilidade. Se um nó falhar devido a problemas de hardware ou software, o balanceador de carga pode redirecionar as solicitações para outros nós, garantindo que a aplicação permaneça acessível.
11. **Escalabilidade**: À medida que a carga de tráfego aumenta, é possível adicionar mais nós ao cluster para escalabilidade horizontal. Isso permite que a aplicação atenda a um número maior de solicitações de maneira eficiente.
12. **Confiabilidade**: A redundância fornecida pela clusterização aumenta a confiabilidade da aplicação, pois os nós adicionais estão prontos para assumir em caso de falha.

Em resumo, a clusterização em servidores de aplicação Java EE / Jakarta EE é uma técnica fundamental para fornecer escalabilidade, alta disponibilidade e confiabilidade em aplicações empresariais. Ela permite que os aplicativos sejam dimensionados e gerenciados de maneira eficaz em ambientes de produção, onde a disponibilidade e o desempenho são cruciais.

Configurar um cluster com 3 nós rodando Wildfly ou JBoss envolve algumas etapas específicas para garantir que os nós se comuniquem efetivamente e compartilhem informações. Aqui estão os passos gerais para configurar um cluster com esses servidores de aplicação e algumas considerações sobre o código da aplicação:

**Configuração do Cluster:**

13. **Instalação e Configuração dos Servidores**: Primeiramente, você deve instalar e configurar o Wildfly ou o JBoss em cada nó do cluster. Isso envolve a configuração das configurações básicas do servidor, como porta HTTP, porta de gerenciamento e outros ajustes específicos da sua aplicação.
14. **Configuração do Gerenciador de Cluster**: O Wildfly e o JBoss usam o **JGroups** como o mecanismo subjacente para a comunicação do cluster. Você precisará configurar o JGroups para seu cluster. Isso geralmente é feito por meio de um arquivo de configuração XML, onde você define o protocolo de transporte, o endereço IP dos nós e outras configurações de comunicação. O arquivo de configuração do JGroups geralmente se chama `**jgroups.xml**`.
15. **Configuração do Subsistema de Web Distribuído (DWS - Distributed Web Subsystem)**: O Wildfly e o JBoss possuem um subsistema específico para tratar da distribuição de sessões web chamado DWS. Você precisará configurá-lo para habilitar o compartilhamento de sessões. A configuração é feita no arquivo `standalone-ha.xml` ou `standalone-full-ha.xml` (ou equivalentes para o domínio) e envolve a definição de um grupo de cluster, um socket-binding-group e a habilitação do subsistema DWS.

**Código da Aplicação:**

16. **Uso de Anotações**: Para tornar a aplicação consciente do cluster, você pode usar anotações específicas de contexto de sessão distribuída, como `@Clustered` ou `@Stateful`. Essas anotações indicam ao servidor de aplicação que determinados componentes de EJB (Enterprise JavaBeans) devem ser compartilhados entre os nós do cluster. Por exemplo:
```java
@Stateful
@Clustered
public class MinhaSessaoDistribuida {
    // ...
}

```
17. **Configuração de Cache**: Se sua aplicação faz uso de caching distribuído (por exemplo, com o uso do Infinispan no Wildfly), você pode configurá-lo para compartilhar informações em cache entre os nós do cluster. Isso é útil para compartilhar dados em cache, como resultados de consulta, entre os nós.
18. **Não Guarde o Estado na Memória**: Evite armazenar estados específicos do nó em memória, pois isso não será compartilhado entre os nós. Use os recursos de sessões distribuídas ou armazenamento compartilhado (por exemplo, um banco de dados) para armazenar dados que precisam ser acessados por todos os nós.
19. **Teste de Cluster**: Ao desenvolver e testar sua aplicação, é importante simular um ambiente de cluster para garantir que tudo funcione conforme o esperado. Você pode configurar vários nós de servidor em sua máquina de desenvolvimento para testar a escalabilidade e a distribuição de sessões.

Lembre-se de que a configuração exata e as considerações de código podem variar dependendo da versão específica do Wildfly ou do JBoss que você está usando, bem como dos requisitos exclusivos da sua aplicação. Consulte a documentação relevante do servidor de aplicação para obter detalhes específicos da configuração e adapte-os à sua situação.

# JBoss 7

- Visão de cloud
- Maior rapidez de inicialização (4s)
- Embora seja possível formar um cluster de alta disponibilidade utilizando várias instâncias em modo standalone, não será possível ter este ponto único de gerenciamento, portanto, a administração de cada nó é feita de forma isolada e repetitiva. O deploy de uma aplicação, por exemplo, deve ser feita em todos os nós do cluster.
- é importante termos em mente que um domínio NÃO é necessariamente um Cluster de Servidores de Aplicação. Embora possa ser utilizado para gerenciar servidores em cluster, o modo Domain não tem nenhuma relação com as características fornecidas por um cluster (alta disponibilidade e balanceamento de carga). O termo domínio está associado ao conceito de gerenciamento de um conjunto de servidores de aplicação. A principal vantagem de se utilizar o AS 7 em modo Domain é a possibilidade de gerenciar configurações e deploys a partir de um ponto central.

![[Untitled 551.png]]

# GlassFish

- Opensource
- derivação do Apache Tomcat
- Implementa toda a especificação Jakarta EE, ou seja, é um Application Server
- Faz uso do componente **Grizzly**, uma biblioteca baseada no Java Non-Blocking I/O (NIO) que exerce um papel fundamental na arquitetura do GlassFish, já que permite o crescimento no número de requisições através de múltiplas *threads*.
- possui suporte à criação de *cluster* e integração com balanceadores de carga para a montagem de ambientes críticos
- Criado pela Sun, atualmente está na Eclipse Foudation
- Em versões anteriores, o GlassFish oferecia suporte a uma característica denominada ***High Availability Database (HADB)***, que era um sistema de armazenamento de dados de sessão distribuído e altamente disponível. No entanto, a partir do GlassFish Server 4.0, esse suporte foi  descontinuado. Agora, para alta disponibilidade de dados de sessão, o GlassFish utiliza outras estratégias como **replicação de sessão em memória** e **armazenamento de sessão em um banco de dados persistente**.
- O GlassFish é conhecido por ser uma das implementações de referência para o Java EE, o que significa que ele serve como um modelo padrão para a implementação dos componentes e funcionalidades dessa plataforma.
- Possui integração com o Java Message Service (**JMS**), o que permite a comunicação baseada em mensagens entre diferentes componentes de uma aplicação distribuída. 
	- Dentro desta integração, o termo *"broker"* refere-se ao componente responsável por gerenciar as mensagens JMS.
	- O **Enhanced Cluster** é um tipo de configuração que oferece maior escalabilidade e disponibilidade para aplicações que utilizam mensagens JMS, através do agrupamento (clustering) de *brokers*. 
	- Esta configuração permite que os *brokers* trabalhem juntos, distribuindo a carga de trabalho e fornecendo redundância, o que significa que **se um *****broker***** falhar, outro pode assumir suas funções, garantindo assim a continuidade dos serviços.**
- o GlassFish oferece a **alta disponibilidade de sessões HTTP**, o que significa que as informações de sessão do usuário podem ser preservadas e acessadas mesmo que ocorra uma falha em uma das instâncias do servidor. 
	- Isso se dá através da replicação de sessão, onde as sessões dos usuários são compartilhadas entre várias instâncias do GlassFish, permitindo que, se uma instância falhar, outra possa assumir sem perda de informação.
	- as conexões de rede em si, que são recursos de mais baixo nível, não são mantidas ou transferidas. Conexões de rede são voláteis e dependem do estado atual do servidor; se o servidor falhar, as conexões de rede estabelecidas por esse servidor são perdidas e novas conexões devem ser estabelecidas.
