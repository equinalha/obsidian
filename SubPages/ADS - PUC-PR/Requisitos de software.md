---
base: "[[ADS - PUC-PR.base]]"
Reviewed: false
Created: 2023-03-22T15:23:00
Status: Not started
Description: ""
---
**Requisitos Funcionais:**

1. Cadastro de usuários: O aplicativo deverá possibilitar que o usuário faça o seu cadastro baseado em seu e-mail, ou através de suas contas no Google, Instagram e Facebook;
2. Agendamento de sessões com tatuadores: Uma vez selecionado o horário e o tatuador desejado, o usuário poderá reservar uma sessão, enviando uma breve descrição do serviço e imagens se desejar;
3. Chat com o tatuador: Possibilidade de enviar dúvidas diretamente para o tatuador selecionado, mesmo antes do agendamento da sessão;
4. Exibição do portfólio dos tatuadores do estúdio: O usuário poderá consultar o portfólio do estúdio, ou filtar por tema, tatuador, estilo, etc.;
5. Listagem de horários disponíveis para agendamento: O usuário poderá consultar a agenda geral ou de algum tatuador específico;
6. Confirmação de agendamento: O usuário poderá confirmar o agendamento, na véspera da data marcada;
7. Cancelamento de agendamento: O usuário poderá desmarcar a sessão a qualquer momento;
8. Feedback: Campo disponível após a sessão para registro do nível de satisfação do usuário e atribuição de nota ao tatuador;
9. Autenticação de usuários: o sistema deve permitir o controle de acesso dos usuários, exigindo que eles se autentiquem antes de utilizar os recursos disponibilizados. Isso garante a segurança das informações e evita acessos não autorizados. 
10. Papéis de usuário: Deverá também existir pelo menos três tipos de usuário no sistema: Clientes, tatuadores e administrador do sistema.

**Requisitos Não-funcionais:**

11. Usabilidade: Interface do usuário intuitiva e fácil de usar;
12. Segurança: Criptografia de dados sensíveis de usuários, como informações de pagamento;
13. Desempenho: Agendamentos rápidos e sistema de resposta ágil;
14. Escalabilidade: Possibilidade de expansão futura do app para outras localidades;
15. Confiabilidade: Disponibilidade constante do aplicativo;
16. Compatibilidade: O aplicativo deve funcionar em diferentes dispositivos móveis.

# Diagramas de caso de uso

- Ator: 
	- reside fora das fronteiras da aplicação
	- Pode ser um usuário, um hardware ou outro software
- Herança:
	- Um ator herda todos os casos de uso do ator mais genérico
	- Representado por uma seta aberta que aponta para a entidade genérica
- Include:
	- O caso de uso incluído executa toda vez que o caso de uso base for chamado
	- Representado por uma linha tracejada e uma seta que aponta para o caso de uso incluído
- Extend:
	- Assim como a herança, este caso de uso pode ser chamado se determinada condição foi atendida
	- Represetado por uma linha tracejada e uma seta que aponta para o caso de uso base
![[SubPages/Concursos/images/Untitled 60.png]]
    ## Especificação de caso de uso.


# Metodologias Ágeis

- Uma história de usuário deve responder a três perguntas: quem, o que e porque. 
- O *backlog* do produto vai conter histórias em diversos níveis diferentes de detalhe. 
- Uma história de usuário se baseia no princípio do cartão (declaração curta), conversa (para alinhamento) e confirmação (critérios de aceitação da história). 
- A história deve ser pequena a ponto de poder ser implementada em uma *sprint*, mas seu entendimento ultrapassa o simples cartão ou Post-it, ela pode conter documentos, fotos ou vídeos adicionais que agreguem entendimento.
- 3 C’s da história de usuário
	- A base das histórias são os 3 Cs: cartão da história de usuário (declaração da história), conversa com os *stakeholders *e confirmação (critérios de aceitação).

## SCRUM

- Entregas menores
- sprints de 1 a 4 semanas
- backlog gerenciado pelo PO
- planejamento feito pela equipe de desenvolvimento
- No SCRUM, o *product owner *é o responsável por gerenciar os itens do *backlog* de produto. 
- O PO é uma pessoa e não um grupo de pessoas. 
- Ele pode até representar um grupo de pessoas ou um comitê. 
- Ninguém tem autoridade para alterar a *sprint*, apenas a equipe de desenvolvimento. 
- O *scrum master* remove impedimentos que atrapalham a realização da *sprint*.  Ele não é um gerente de projetos, pois a ideia é que a equipe SCRUM seja autogerenciada e autônoma. 
- O *scrum master* não é o único canal de comunicação com o *product owner.*

# Verificação de requisitos

- Elicitação
- Análise
- Especificação
- Validação
	- Validação: Se o requisito atendeu
	- Verificação: Se sendo construído corretamente