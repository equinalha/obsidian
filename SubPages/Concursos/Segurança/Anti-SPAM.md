---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-09-13T09:49:00
Owner:
  - Eduardo Quinalha
---
# Blacklists

- As **listas negras de IPs** bloqueiam servidores conhecidos por enviar SPAM. 
- Provedores de e-mail consultam essas listas antes de aceitar ou entregar uma mensagem.
- Serviços populares como **Spamhaus** mantêm essas listas, e servidores de e-mail as utilizam para bloquear remetentes com má reputação.
- Além de IPs, essas listas podem conter domínios, URLs e outros identificadores.

# Graylists

- Técnica que temporariamente rejeita o primeiro envio de e-mails de um remetente desconhecido. 
- A maioria dos servidores legítimos tentará enviar o e-mail novamente após um curto intervalo.
- Servidores de SPAM, no entanto, muitas vezes não reencaminham o e-mail, resultando na rejeição da mensagem.

# SPF

- protocolo de autenticação de e-mail que permite que o proprietário de um domínio especifique quais servidores de e-mail estão autorizados a enviar mensagens em nome desse domínio
- O administrador de um domínio publica um registro **TXT** no **DNS (Domain Name System)** do domínio. 
- Esse registro contém uma lista de endereços IP ou nomes de servidores que estão autorizados a enviar e-mails em nome daquele domínio.
```plain text
exemplo.com IN TXT "v=spf1 ip4:192.0.2.0/24 include:_spf.google.com -all"
```
	- **v=spf1**: Indica a versão do SPF.
	- **ip4:192.0.2.0/24**: Permite qualquer IP dentro desse bloco (192.0.2.0 a 192.0.2.255) a enviar e-mails para o domínio.
	- **include:_spf.google.com**: Permite que servidores autorizados pelo SPF de Google também enviem e-mails em nome do domínio.
	- **all**: Qualquer servidor que não esteja listado explicitamente no registro SPF deve ser rejeitado.
- Quando um e-mail é enviado, o servidor de recepção (o servidor que está recebendo o e-mail) verifica o domínio no cabeçalho "MAIL FROM" (ou envelope sender) e consulta o **registro SPF** associado a esse domínio no DNS.
- O servidor receptor compara o endereço IP do servidor que enviou o e-mail com os endereços listados no registro SPF. 
- Com base nessa verificação, o servidor receptor decide como tratar o e-mail.

# DKIM

- protocolo de autenticação de e-mail que permite ao destinatário verificar se o e-mail foi realmente enviado e autorizado pelo domínio de origem e **se o conteúdo não foi alterado durante o trânsito.**
- usa **criptografia de chave pública** para assinar digitalmente partes do e-mail, garantindo a integridade da mensagem e a autenticidade do remetente.
- **Assinatura de Mensagem (Lado do Remetente)**:
	- O servidor de e-mail que envia a mensagem (associado ao domínio do remetente) **assina digitalmente o e-mail usando uma chave privada.**
	- Essa assinatura é aplicada a** partes específicas da mensagem** (geralmente o corpo e alguns cabeçalhos, como "From", "To", "Subject").
	- A assinatura é adicionada ao **cabeçalho da mensagem em um campo especial chamado DKIM-Signature.**
- **Publicação da chave pública no DNS**
	- Para verificar a assinatura, o destinatário precisa da **chave pública** correspondente. 
	- Essa chave pública é publicada como um registro **TXT** no **DNS** do domínio do remetente.
- **Verificação da Assinatura (Lado do Destinatário)**
	- Quando o servidor de e-mail do destinatário recebe a mensagem, ele verifica o cabeçalho **DKIM-Signature**.
	- O servidor faz uma consulta DNS para obter a **chave pública** correspondente ao domínio do remetente e ao seletor especificado.
	- Usando essa chave pública, o servidor de e-mail do destinatário verifica se a assinatura DKIM é válida e se a mensagem não foi modificada durante o trânsito.

# DMARC

- destina-se a ajudar a combater a fraude por correio eletrónico e os ataques de phishing
- Não é considerado uma solução Anti-spam mas sim um** protocolo de autenticação de correio eletrônico**
- Baseia-se em SPF e DKIM
- Funcionamento
	- O DMARC utiliza o **SPF **e o **DKIM **para verificar a autenticidade dos e-mails.
		- **SPF** verifica se o e-mail foi enviado de um **servidor autorizado pelo domínio do remetente.**
		- **DKIM** usa assinaturas digitais para garantir que o conteúdo do e-mail não foi alterado durante o trânsito.
	- Para que uma mensagem passe na verificação DMARC, o domínio do cabeçalho "From:" deve estar **alinhado** com os domínios verificados pelo SPF ou DKIM.
		- **Alinhamento Estrito**: O domínio do SPF/DKIM deve ser exatamente o mesmo que o do cabeçalho "From:".
		- **Alinhamento Relaxado**: O domínio do SPF/DKIM pode ser um subdomínio do domínio "From:".
	- O dono do domínio define uma política de DMARC que especifica como os provedores de e-mail devem tratar os e-mails que falharem nas verificações de autenticação:
		- **none**: Nenhuma ação é tomada, mas relatórios de falhas são enviados ao administrador do domínio.
		- **quarantine**: O e-mail que falha é colocado na pasta de spam.
		- **reject**: O e-mail que falha é completamente rejeitado e não entregue ao destinatário.
	- Um registro **DMARC** é configurado como um **registro TXT** no DNS do domínio: 
```plain text
_dmarc.exemplo.com IN TXT "v=DMARC1; p=quarantine; rua=mailto:dmarc-reports@exemplo.com; ruf=mailto:dmarc-reports@exemplo.com; fo=1"
```
		- **v=DMARC1**: Versão do DMARC.
		- **p=quarantine**: A política indica que e-mails que falharem devem ser colocados na pasta de spam.
		- **rua**: Endereço de e-mail para receber relatórios agregados.
		- **ruf**: Endereço de e-mail para receber relatórios detalhados (forensic).
