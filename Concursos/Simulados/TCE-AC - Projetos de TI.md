---
base: "[[Simulados.base]]"
Desempenho: 0.65
Banca: CEBRASPE
Obs: ""
Tipo: Certo/Errado
Obj: TSE
"% Colocação": -100
Status: Done
Data: 2024-10-22
---
# Anotações e Erros

**51 - *****Sprint planning***** é a reunião em que a equipe de desenvolvimento define o objetivo da *****sprint *****e seleciona os itens do *****product backlog***** que serão trabalhados.**

> Gabarito da banca: C

*O Product Owner propõe como o produto pode aumentar seu valor e utilidade na Sprint atual. ****Todo o Scrum Team então colabora para definir uma Meta da Sprint ****que comunica porque a Sprint é valiosa para os stakeholders. A meta da Sprint deve ser finalizada antes do final da Sprint Planning.*

**70 - Na notificação por *****push*****, os métodos de autenticação de dois fatores (2FA) exigem uma senha para aprovar o acesso a um sítio ou aplicativo. **

> Gabarito: E

Notificação por push pode ser aquela onde o usuário apenas toca em Sim ou Não em seu smartphone.

**71 - O OpenID Connect é um protocolo de identidade simples, construído no protocolo do JSON Web Token, e permite que os aplicativos clientes confiem na autenticação executada por um provedor OpenID Connect para verificar a identidade de um usuário. **

> Gabarito - E

JSON Web Token é o formato do token e não o protocólo. O correto seria OAuth 2.0

**88 - O plano de gerenciamento do escopo é o documento de entrada do processo em que se faz o controle do escopo do projeto, o qual integra a fase de encerramento do projeto.**

> Gabarito: E

O plano de gerenciamento do escopo é um documento que faz parte do processo de planejamento e não da fase de encerramento do projeto. Ele define como o escopo do projeto será definido, validado e controlado ao longo de todo o ciclo de vida do projeto. O controle do escopo do projeto ocorre durante a execução e monitoramento, onde se assegura que todas as entregas estão de acordo com o escopo acordado, e quaisquer mudanças são devidamente gerenciadas.
> A fase de **encerramento do projeto** foca na verificação das entregas, conclusão dos trabalhos e obtenção de aceitação formal, mas o controle do escopo ocorre de maneira contínua antes dessa fase.

**90 - Em uma estrutura genérica do ciclo de vida de um projeto, o risco é menor no início do projeto e aumenta gradativamente ao longo do tempo de desenvolvimento do projeto.**

> Gabarito: E

Os riscos são maiores no início e **diminui gradativamente** conforme o projeto avança. Isso ocorre porque, no início, há mais incertezas e variáveis desconhecidas.

**98 - AJAX representa técnicas utilizadas para que páginas web sejam carregadas rapidamente pelo processamento na parte cliente da aplicação. **

> Gabarito: E

O objetivo do AJAX não é acelerar o carregamento de páginas web, mas sim para torná-las dinâmicas

**106 - No código apresentado, o termo *****name *****é um elemento e o termo *****message *****é uma *****tag*****. **

```xml
<message name=“getTermRequest”>
 <part name=“term” type=“xs:string”/>
</message>
<message name=“getTermResponse”>
 <part name=“value” type=“xs:string”/>
</message>
<portType name=“glossaryTerms”>
 <operation name=“getTerm”>
 <input message=“getTermRequest”/>
 <output message=“getTermResponse”/>
 </operation>
</portType>
<binding type=“glossaryTerms” name=“b1”>
 <soap:binding style=“document”
transport=“http://schemas.xmlsoap.org/soap/http” />
 <operation>
 <soap:operation
soapAction=“http://example.com/getTerm”/>
 <input><soap:body use=“literal”/></input>
 <output><soap:body
use=“literal”/></output>
 </operation>
</binding>
```

> Gabarito: C
Meu gabarito: E

name não é um elemento, mas sim um atributo.
message de fato é uma tag

> - **Tag**: É apenas a marcação usada para abrir ou fechar um elemento (`<nome>`, `</nome>`).
> - **Elemento**: É a estrutura completa que inclui a tag de abertura, o conteúdo (se houver), e a tag de fechamento.

109 - *Na sprint planning*, fica a critério exclusivo dos *developers *o planejamento necessário para se criar um incremento que atenda à definição de pronto, o que pode ser realizado decompondo-se os itens do *product backlog*.

> Gabarito: C

De fato, está no guia:

> *Para cada item do Product Backlog selecionado, os Developers planejam o trabalho necessário para criar um Incremento que atenda à Definição de Pronto. Isso geralmente é feito decompondo itens do Product Backlog em itens de trabalho menores de um dia ou menos. A forma como isso é feito fica ****a critério exclusivo dos Developers**** . Ninguém mais diz a eles como transformar itens do Product Backlog em incrementos de valor.*