---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:40:00
Owner:
  - Eduardo Quinalha
---
[https://www.redhat.com/pt-br/topics/automation/what-is-infrastructure-as-code-iac](https://www.redhat.com/pt-br/topics/automation/what-is-infrastructure-as-code-iac)

# Características

- Provisionamento automatizado do ambiente
- Permite o versionamento
> *O controle de versão é uma parte importante da IaC. Os arquivos de configuração devem pertencer à fonte como qualquer outro código-fonte de software. Ao implantar a infraestrutura como código, também é possível separá-la em módulos, que podem ser combinados de diferentes maneiras por meio da automação.*

# Categorias

## Orquestração

- Provisiona e gerencia componentes do ambiente (recursos em cloud, por exemplo)
- Exemplos: Terraform, AWS CloudFormation

## Gerenciamento de configuração

- Instalam, atualizam e administram o software em execução em servidores
- Exemplos: Puppet, Chef, Ansible
- De certa forma, inclui-se o kubernetes também

# Abordagens

- **IaC Declarativa**
	- Define o estado desejado do sistema
	- Mantém uma lista do estado atual dos objetos do seu sistema
- **IaC Imperativa**
	- Define os comandos que serão inseridos para se obter o resultado desejado
	- Exige o conhecimento sobre como fazer
- As ferramentas de IaC costumam suportar as duas abordagens, porém com preferência por uma delas

# Principais Ferramentas

- Chef
- Puppet
- [Ansible](https://www.redhat.com/pt-br/topics/automation/learning-ansible-tutorial)
- Saltstack
- Terraform

# Ansible

- Conecta aos nós e envia pequenos programas chamados módulos
- Os módulos são executados e removidos ao terminar
- Módulos podem ser escritos em qualquer linguagem que retorne um JSON:
	- Ruby, Python ou bash
- Ansible não depende de agentes, ele utiliza SSH
- Utiliza templates **YAML**

## Componentes

### Playbooks

- Usados para orquestrar processos de TI
- Trata-se de um arquivo YAML contendo um ou mais **plays**
- Usando para definir o estado desejado de um sistema
- Um módulo é um script autônomo que pode ser utilizado dentro do playbook
- **Playbooks são idempotentes.**
- Isso quer dizer que a repetição de sua execução, e de suas tarefas, independentemente do número de vezes, sempre reproduzirá o
mesmo estado.
- O objetivo é evitar alterações adicionais se o estado desejado já estiver alcançado.

### Plays

- Conjunto ordenado de tarefas a serem executadas em hosts selecionados
- Associado a um objetivo, por exemplo, atualizar o Apache

### Tasks

- Etapas distintas dentro de uma play

### Module

- Uma capacidade distinta do Ansible, plugins
- Cada módulo é um script autônomo que é executado pelo Ansible em um ou mais nós, aplicando uma mudança, verificando um estado, ou coletando informações.
- Quando um playbook é executado, o Ansible envia o módulo necessário para o nó remoto, executa-o e captura o resultado.
- Os modules podem ser escritos em qualquer linguagem que retorne JSON, como Ruby, Python ou bash
- São customizáveis
- São eles que efetivamente entendem a configuração desejada e executam os comandos no host

![[SubPages/Pessoal/images/image 61.png|Ansible Playbook]]

- **Tipos de módulos**
	- **Módulos de ação**, que realizam ações específicas nos nós, como instalação de pacotes;
	- M**ódulos de estado**, que verificam ou impõem um estado de um recurso;
	- **Módulos de fatos**, que coletam informações sobre os nós;

### Inventário

- arquivo centralizado que visa organizar os nós gerenciados
- delimita com quais nós o Ansible irá trabalhar
- aponta características do sistema e a localização do nó gerenciado
- Formas:
	- Inventário estático
		- Tipo mais comum
		- Definido em arquivo texto INI ou YAML
```plain text
[myhosts]
192.0.2.50
192.0.2.51
192.0.2.52
```
		- Lista os hosts e grupos
```yaml
all:
  children:
    campus_a:
      children:
        web:
          hosts:
            web01a:
              ansible_host: 192.168.1.101
            web02a:
              ansible_host: 192.168.1.102
        db:
          hosts:
            db01a:
              ansible_host: 192.168.1.201
    campus_b:
      children:
        web:
          hosts:
            web01b:
              ansible_host: 192.168.2.101
        db:
          hosts:
            db01b:
              ansible_host: 192.168.2.201
```
	- Inventário dinâmico
		- Usando principalmente em ambientes dinâmicos como nuvens, onde a lista de hosts pode mudar com frequência
		- Gerado por scripts e plugins que consultam fontes externas

### Roles

- componente essencial no Ansible para organizar e reutilizar código
- permitem que os usuários agrupem tarefas, handlers, arquivos, templates, variáveis e até mesmo outros módulos do Ansible de forma modular
- basicamente mapeia os códigos já criados e mantém uma espécie de biblioteca que permite reutilizar códigos criados de maneira mais rápida e concisa
- Para utilizar uma role em um playbook, simplesmente incluímos a role na seção roles da play.
- Isso instrui o Ansible a aplicar todas as tarefas e configurações definidas na role aos hosts especificados na play

## Ansible Galaxy

- Repositório público para compartilhamento de roles
- As roles disponibilizadas podem ser instaladas usando o comando `ansible-galaxy`

## Vault

- Funcionalidade que permite criptografar dados sensíveis, como senhas, chaves e outras informações confidenciais, para que possam ser armazenados de forma segura dentro dos playbooks ou outros arquivos usados no Ansible.
- Utiliza o algoritmo de criptografia simétrica AES (Advanced Encryption Standard) com uma chave de 256 bits
- É possível criptografar um arquivo inteiro ou apenas variáveis específicas dentro de um arquivo YAML.
- Para criptografar um arquivo inteiro, usamos o comando `ansible-vault encrypt <arquivo>`, 
- Para criptografar apenas uma parte do arquivo, utilizamos o` !vault`.

## Templates

- São arquivos que contêm conteúdo dinâmico que pode ser gerado ou modificado conforme as variáveis e o contexto da execução do playbook
- Baseados na linguagem de template **Jinja2**, que permite a inserção de lógica condicional, loops, filtros e a utilização de variáveis para criar arquivos de configuração ou outros tipos de conteúdo que precisam ser personalizados conforme o ambiente ou a execução específica
- Um dos principais usos dos templates é a **substituição de variáveis nos arquivos de configuração**
- Esses arquivos contêm o conteúdo base que será gerado e as marcações Jinja2 que indicam onde o conteúdo dinâmico será inserido
- Para utilizar templates no Ansible, usamos o módulo template

## Ansible Tower

- interface gráfica, API RESTful e mecanismo de automação que expande as capacidades do Ansible
- particularmente útil em ambientes onde a automação precisa ser gerenciada e auditada de forma centralizada.

## Arquitetura

- Envolve:
	- Nó de controle
	- Nós gerenciados
- O controle de quais nós são monitorados é feito através de um artefato denominado Inventário (Inventory).

![[SubPages/Pessoal/images/image 62.png]]

## Comandos

- `ansible <host_pattern> -m <module_name>`
	- `<host_pattern>`: Um padrão que corresponde aos hosts no inventário do Ansible. Isso pode ser:
		- O nome de um **grupo de hosts** definido no arquivo de inventário
		- O nome de um **único host.**
		- Um padrão que abrange vários hosts (por exemplo, `web*` para selecionar todos os hosts cujo nome comece com "web").
	- `m <module_name>`: A opção `m` especifica qual módulo Ansible deve usar. 
		- O Ansible possui uma vasta coleção de módulos para realizar várias tarefas, como `ping`, `command`, `shell`, `copy`, `yum`, entre outros.
- `ansible-playbook <arquivo_playbook>.yml`
	- Isso executa o playbook em todos os hosts definidos no inventário
- `ansible-playbook <playbook_file>.yml -l <host>`
	- Para executar um **playbook** em um host específico, você pode utilizar a opção `-l` (ou `--limit`) no comando `ansible-playbook`
- `ansible-inventory --list`
	- exibe todos os hosts e grupos definidos no inventário

# Terraform

- Linguagem de IaC declarativa
- Uma configuração terraform pode ser composta de múltiplos arquivos e diretórios
- geralmente usa **SSH** para executar scripts de shell em ambientes Linux/Unix.
- Os arquivos de configuração são escritos em HashiCorp Configuration Language (HCL)
- Antes de aplicar qualquer mudança na infraestrutura, o Terraform gera um plano que mostra o que será alterado
- Suporta uma grande variedade de provedores de nuvem, como AWS, Azure, Google Cloud, além de provedores de serviços locais e especializados.
- Estrutura básica

```hcl
resource "aws_vpc" "main" {
  cidr_block = var.base_cidr_block
}

<BLOCK TYPE> "<BLOCK LABEL>" "<BLOCK LABEL>" {
  # Block body
  <IDENTIFIER> = <EXPRESSION> # Argument
}
```

## Providers

- Responsáveis por interagir com as APIs dos diferentes serviços que o Terraform pode gerenciar. 
- Cada provedor permite ao Terraform gerenciar recursos de um serviço ou plataforma específica, como AWS, Azure, Google Cloud, Kubernetes, etc.
- Exemplo de provedores: `aws`, `azurerm`, `google`, `kubernetes`.

## Provisioners

- Executam os comandos dentro do recurso provisionado
- Principais provisioners
	- **remote-exec**
		- Execut comandos em um recurso remoto como uma VM, por exemplo.
		- Conecta ao recurso via SSH ou WinRM (sistemas baseados em Windows)
	- **local-exec**
		- Executa comandos no local onde o Terraform está sendo executado
	- **file**
		- Usado para copiar arquivos ou diretórios do sistema local para o recurso remoto
	- **chef**
		- Interage com a plataforma Chef (CI/CD)
	- **puppet**
		- Interage com a plataforma Puppet

## Recursos

- componentes fundamentais que você cria e gerencia com o Terraform. 
- Eles representam objetos reais na infraestrutura, como instâncias de máquinas virtuais, redes, bancos de dados, e outros.

```hcl
resource "aws_instance" "example" {
  ami           = "ami-123456"
  instance_type = "t2.micro"
}
```

### **Blocos de Configuração (Configuration Files)**

- Esses são os arquivos onde você escreve o código declarativo do Terraform. 
- Normalmente têm a extensão `.tf` e são escritos em HCL (*HashiCorp Configuration Language*). 
- Esses arquivos contêm definições de recursos, provedores e variáveis.

## Arquivos

- `.tfstate`
	- Armazenam o estado atual da infraestrutura provisionada pelo Terraform
- `.tf`
	- Os provedores de nuvem e módulos customizados são especificados nos arquivos de configuração do Terraform (.tf)

## Saídas

- Permitem exportar valores calculados como endereço IP, por exemplo

```hcl
output "instance_ip" {
  value = aws_instance.example.public_ip
}
```

## Variáveis

- Podem ser definidas diretamente no arquivo de configuração, passadas por linha de comando ou armazenadas em arquivos separados

```hcl
variable "instance_type" {
  default = "t2.micro"
}
```

## Bloco Terraform

- Usado para configurar aspectos globais da execução do Terraform
- Um exemplo é o backend para armazenar o estado

```hcl
terraform {
  backend "s3" {
    bucket = "my-terraform-state"
    key    = "state/terraform.tfstate"
    region = "us-west-2"
  }
}
```

## Principais comandos

- `terraform init`: Inicializa o ambiente de trabalho e baixa os provedores necessários.
- `terraform plan`: Gera um plano mostrando o que o Terraform irá mudar na infraestrutura.
- `terraform apply`: Aplica as mudanças e cria ou modifica os recursos.
- `terraform destroy`: Remove os recursos gerenciados pelo Terraform.

## Exemplo prático

```hcl
# Configurando o Provedor AWS
provider "aws" {
  region = "us-west-2"  # Altere para a sua região preferida
}

# Criando uma VPC
resource "aws_vpc" "my_vpc" {
  cidr_block = "10.0.0.0/16"
}

# Criando uma Subnet
resource "aws_subnet" "my_subnet" {
  vpc_id            = aws_vpc.my_vpc.id
  cidr_block        = "10.0.1.0/24"
  availability_zone = "us-west-2a"  # Altere conforme sua região
}

# Criando um Gateway de Internet
resource "aws_internet_gateway" "my_igw" {
  vpc_id = aws_vpc.my_vpc.id
}

# Criando uma Tabela de Rotas
resource "aws_route_table" "my_route_table" {
  vpc_id = aws_vpc.my_vpc.id

  route {
    cidr_block = "0.0.0.0/0"
    gateway_id = aws_internet_gateway.my_igw.id
  }
}

# Associação da Tabela de Rotas à Subnet
resource "aws_route_table_association" "my_route_table_assoc" {
  subnet_id      = aws_subnet.my_subnet.id
  route_table_id = aws_route_table.my_route_table.id
}

# Criando uma Instância EC2
resource "aws_instance" "my_ec2" {
  ami           = "ami-0c55b159cbfafe1f0"  # Ubuntu 20.04 AMI (substitua por um AMI adequado à sua região)
  instance_type = "t2.micro"
  subnet_id     = aws_subnet.my_subnet.id

  tags = {
    Name = "MyTerraformInstance"
  }
}

# Saída do endereço IP da instância
output "instance_ip" {
  value = aws_instance.my_ec2.public_ip
}
```

## Fases de Execução

- Write
- Plan
- Apply

## Principais comandos

![[SubPages/Pessoal/images/image 63.png]]