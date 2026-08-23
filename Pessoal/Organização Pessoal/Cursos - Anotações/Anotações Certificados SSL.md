---

---
# Tipos

- **EV (Extended Validation):** Oferece o maior grau de proteção. Mais difícil de se obter, seu processo envolve requerimentos técnicos e legais;
- **OV (Organizational Validation): **Validação de propriedade do domínio. Exibe um selo de segurança na barra de endereços
- **DV (Domain Validation):** Tipo mais popular, mais barato e fácil de obter. (Let’s encrypt). Valida a propriedade do domínio, mas não necessita de informações legais sobre a organização.

# Como funciona?

A assinatura digital (hash) garante que ele não teve suas informações alteradas. Este hash passa pela chave privada.

A chave pública serve para criptografar dados que somente a organização detentora do certificado pode de-criptografar com sua chave privada.

Sites HTTPS recebem mais visibilidade em mecanismos de busca

# Curso Lets Encrypt + Digital Ocean

- Criar conta e novo droplet na digital Ocean
- Em Networking, adicionar o domínio
- No registro.br, configurar os name Servers conforme os fornecidos no Digital Ocean
- No Digital Ocean, em domains, adicionar um registro “A”, contendo um “@” e apontando para o droplet
- Adicionar também um CNAME “www” como alias de “@”
- No servidor (droplet) configurar o /etc/hosts adicionando o IP da instância (fornecido pela DO) como alias do domínio


```shell
# Your system has configured 'manage_etc_hosts' as True.
# As a result, if you wish for changes to this file to persist
# then you will need to either
# a.) make changes to the master file in /etc/cloud/templates/hosts.debian.tmpl
# b.) change or remove the value of 'manage_etc_hosts' in
#     /etc/cloud/cloud.cfg or cloud-config from user-data
#
127.0.1.1 myserver myserver
127.0.0.1 localhost
159.65.234.238 isabelsoares.psc.br

# The following lines are desirable for IPv6 capable hosts
::1 localhost ip6-localhost ip6-loopback
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

- Configurar a timezone da seguinta forma


```shell
dpkg-reconfigure tzdata
```

- Instalar o client do Lets Encrypt (certbot)
- rodar o letsencrypt

```javascript
letsencrypt --apache -d <dominio.com>

# ou

sudo certbot certonly --standalone
```

# Analise do certificado

```javascript
https://www.ssllabs.com/ssltest/analyze.html?d=<dominio.com>
```

# Atualização via crontab

```shell
30 3 * * 1 /usr/bin/certbot renew >> /var/log/le-renew.log
```