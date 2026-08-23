---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2025-05-06T16:05:00
Owner:
  - Eduardo Quinalha
---
# Conceitos básicos

Também conhecidos como:

- VCS - Version Control System
- SCM - Source Code Management

## Vantagens

- Controle do histórico
	- resgate de versões mais antigas e estáveis
	- análise das alterações
- Trabalho em equipe
	- Minimiza conflitos de edições
	- Controle de acesso por usuário ou grupo
- Marcação e resgate de versões estáveis
	- Divisão em linhas de desenvolvimento
	- Trabalho em paralelo
- Segurança
- Rastreabilidade
- Organização
- Confiança
	- Repositórios remotos na nuvem

## Tipos

- VCS → local
	- Controle de versão local
- CVCS → Centralizado
	- Permite o trabalho em equipe
	- Ponto único de falha
- DVCS → Distribuído
	- Cada repositório local é de fato um backup completo do repositório e pode ser utilizado para restaurá-lo em caso de falha

# git

> [!tip] 💡
> Possíveis questões de concurso:

O git commit com a flag -a permite comitar as alterações de arquivos **que já estão sendo rastreados. **Este flag **não trackeia novos arquivos**. Para estes casos, ainda faz-se necessário um **git add** primeiro

A diferença entre git fetch e git pull é que o fetch puxa as alterações mas não aplica, o pull já aplica tudo

O git checkout não consegue desfazer alterações que já estejam na staging area. Para isso, utiliza-se git reset

A principal diferença entre o git e outros sistemas de controle de versões está na forma como o git trata seus dados

## Características

Os outros sistemas, armazenam os arquivos originais e um delta (alterações) sobre estes arquivos ao longo do tempo.

![[Untitled 800.png]]

- O git armazena uma imagem do sistema de arquivos em miniatura

![[Untitled 801.png]]

- O git armazena tudo em seu banco local, não pelo nome do arquivo, mas pelo hash do seu conteúdo
- O hash do git é calculado pela função SHA1 e é composto por 40 caracteres hexadecimais
- O git somente adiciona dados, nada é perdido

## Estados

- Commited
- Staged
- Modified

![[Untitled 802.png]]

## Diretório .git

- O diretório .git é onde ficam armazenados os metadados e o banco de dados de objetos do projeto
- Este é o diretório copiado quando se clona um repositório
- O diretório de trabalho é uma cópia de uma versão do projeto armazenado nesta pasta
	- Os arquivos são descompactados a partir do banco de dados que encontra-se no .git
- A área de preparo (staging area) é um arquivo contendo uma lista dos arquivos que serão adicionados no próximo commit

## Comandos Básicos

```bash
# Comitar um arquivo mesmo quando está no gitignore
git add -f arquivo_no_gitignore.txt

# Exibir histórico com diff das duas últimas alterações
git log -p -2

# Exibir resumo do histórico
git log --stat

# Exibir revisão e autor da última modificação de uma bloco de linhas
git blame -L 12,22 meu_arquivo.txt

# Alterando a mensagem do commit
git commit --ammend

# Mostra as alterações entre o último commit e a stagind area
git diff

# Desfazer as últimas alterações de um arquivo, ainda não commitado
git checkout arquivo.txt

# Desfazendo alterações, já commitado
# Esta forma, não apaga o commit indesejado, mas coloca-se o commit anterior na frente na linha do tempo, como se fosse um novo commit.
# Antes: C1 -> C2 -> C3 (commit ruim)
# Depois: C1 -> C2 -> C3 -> C4 = C2 (revertido)
git revert <HASH do commit ruim>

# Desfazendo um commit, apagando do histórico
# Antes: C1 -> C2 -> C3 (commit ruim)
# Depois: C1 -> C2
git reset --hard <HASH do último commit bom>

# TAG
# Cria um release do projeto, uma foto daquele instante do tempo, tornando possível acessá-la posteriormente
git tag -a 1.0.0 -m "Concluída versão 1.0.0"

# Stash - Utilizado para jogar as alterações atuais em uma área temporária (WIP - Work in progress), permitindo fazer outra alteração a partir do último 
# commit
# Uma vez concluída a alteração e comitada, pode-se retornar ao ponto que estava retirando as alterações desta área temporária
git stash

# Consultando
git stash list

# Retornando
git stash apply

# Transformando o stash em um branch
git stash branch <branchname>

# Log vs RefLog
# Log faz um tracking dos commits
# Reflog exibe tudo o que foi feito no repositório local

# log -p -> Já traz um diff das alterações

# Visualização Gráfica das Branches
git log --graph --all --decorate
```

```bash
# Commit com flag -a
git commit -a -m "comentário"
```

## Branches

- No git, um branch é na prática um ponteiro para um commit
- Cada commit tem um ponteiro que aponta para seu commit “pai”
- Por exemplo:
	- Pode-se criar uma nova branch de forma manual, voltando-se o HEAD para um commit anterior: `git checkout <commit>`
	- Então criar um novo commit a partir dali (terá feito a ramificação)

```bash
# Listando branches
git branch -a

# Criando uma nova branch a partir da master, preservando o mesmo último commit
git checkout -b <nova branch>

# Mudando de branch
git checkout <nome da branch>

# Merge Fast Forward -> Quando os commits da branch são "mergeadas" no master, sem que tivesse havido nenhuma alteração neste meio tempo. Faz apenas uma
# cópia dos commits da branch, colocando-os na sequencia do master
# Como não 
```

## Merge

### Merge Fast Forward

Quando os commits da branch são "mergeadas" no master, sem que tivesse havido nenhuma alteração neste meio tempo. Faz apenas uma cópia dos commits da branch, colocando-os na sequencia do master. 

```bash
# Mudando da branch secundária para a branch master
git checkout master

# Fazendo o merge
git merge <branch secundária>
```

![[Untitled 803.png|Merge Fast Forward]]

### Merge commit

![[Untitled 804.png]]

### Merge com conflito

Como boa prática, os conflitos são resolvidos na branch secundária.

```bash
# 1- Na branch secundária, puxar um merge das alterações da branch master
git merge master

# 2- O git vai sinalizar o conflito! Os pontos conflitantes ficam marcados por texto dentro do arquivo. Basta editá-lo e resolver o problema
# 3- Adicionar as alterações para área staged
git add .

# 4- Criar o commit de resolução de conflito
git commit -am "Resolução de conflito de merge"

# 5- Voltar para a branch master e fazer o merge, que agora deverá ser um fastforward
git checkout master
git merge <branch secundária>
```

## Movimentando commits e branches

- É possível movimentar pelos commits de algumas formas:
	- `git checkout <branch>` → Volta o HEAD para o ponto onde estava no branch desejado
	- `git checkout <commit>` → Movimenta o HEAD para o commit indicado
	- `git branch -f <brach> <commit>` → Movimenta a branch especificada para o comit desejado
- Movimentação relativa
	- `git checkout HEAD^` → Movimenta para um nível acima do HEAD
		- Quando utilizado seguido por um número, pode especificar para qual nó pai ele irá: `HEAD^2`
	- `git branch -f <branch> HEAD~3` → Movimenta a branch para 3 commits acima da localização atual do HEAD

<!-- Column 1 -->
- Exemplo:
	- Partindo de:
	- Para chegar em:
![[Untitled 805.png]]
```bash
git branch -f bugFix HEAD~2
git branch -f main c6
git checkout c1
```
- Rebase
	- Cria uma cópia do commit e coloca na sequência em outra branch
	- `git rebase <branch de destino>`
		- a partir da referencia atual (HEAD) envia este commit para o branch de destino especificado
	- `git rebase <destino> <origem>`
		- reorganiza a branch de origem a partir do destino especificado
	- Diferente do merge, onde se especifica a outra branch
	- `git merge <branch de origem>`
- Interactive Rebase
	- Permite reorganizar os commits de forma interativa
	- Funciona via um editor de texto, como VIM
	- Deve ser especificado um commit anterior, a partir do qual os commits serão reorganizados
	- `git rebase -i <referencia>` por exemplo `git rebase -i HEAD~4`
- Cherry Pick
	- Permite selecionar commits específicos e colocar cópias destes na sequência da referência atual
	- o git cherry-pick copiará um commit de qualquer lugar na árvore sob o HEAD (desde que esse commit não seja um ancestral do HEAD).
	- `git cherry-pick <commit 1> <commit 2> <…>`

<!-- Column 2 -->
![[Untitled 806.png]]

## Git Reset vs Git Revert

- Reset
	- Desfaz o commit apenas voltando no tempo
	- Na prática, move a referência para um commit anterior
	- Validade no repositório local
	- Pode causar conflito se enviada para o repositório remoto
	- `git reset <commit de destino>`
	- Também pode ser utilizado para remover um arquivo da stage area antes de um commit
```bash
# Retira um arquivo da stage area antes de realizar o commit
git reset HEAD <file>
```
![[Untitled 807.png]]
	- Formas de uso:
```bash
# Volta o HEAD para o commit anterior, mantém a stage area (index) e o working directory com as últimas alterações
git reset --soft HEAD~

# Volta o HEAD para o commit anterior, volta a stage area (index) para refletir o commit anterior, 
# mantém o working directory com as últimas alterações
# Obs: git reset <ref> = git reset --mixed <ref>
git reset HEAD~

# Volta HEAD para o commit anterior, volta a stage area (index) para refletir o commit anterior,
# volta o working directory para refletir o commit anterior
git reset --hard HEAD~
```
	- Explicando graficamente:
![[Untitled 808.png|Situação inicial]]
![[Untitled 809.png]]
![[Untitled 810.png]]
![[Untitled 811.png]]
- Revert
	- Desfaz o commit criando um novo commit com as alterações necessárias para isso
	- Ao ser enviado para o repositório remoto possibilitará desfazer as alterações do commit
	- `git revert HEAD`
		- Desfaz a alteração do commit onde encontra-se a referência (HEAD)
		- O commit de reversão será posicionado na sequência de onde a referência está atualmente
- Ammend
	- Torna possível alterar um commit já realizado
	- Pega o que tem na stage area e adiciona ao último commit
	- Se não tiver nada em stage, somente altera a mensagem do commit
	- Exemplo: 
```bash
$ git commit -m 'initial commit'
$ git add forgotten_file
$ git commit --amend
```
- **Desfazendo as Modificações de um Arquivo**
```bash
# Desfaz as alterações do arquivo para como ele era após o último commit
git checkout -- <file>
```

## Tags

- Os marcadores das branches se movimentam constantemente pelos commits
- Uma forma de criar uma referência definitiva é por meio de tags
- `git tag <tag> <commit>`

![[Untitled 812.png]]

## Estratégias de Merge

- **Merge Commit**
	- Cria um novo commit que incorpora as alterações de outro branch. Mesmo que os commits sejam compactados ao mesclar, um commit de merge separado é sempre criado
- **Three-way Merge**
	- Compara os dois branches e o commit que é ancestral comum dos dois. Se não houver conflito, aplica as mudanças introduzidas pelos dois branches em um novo commit.
- **Squash and Merge**
	- Combina todos os commits do branch de recurso em um único e mescla com o padrão
- **Fast-Forward Merge**
	- Ocorre quando o *branch *de destino não possui novos *commits *desde o ponto em que o *branch *de origem divergiu. Nesse caso, o Git simplesmente avança o ponteiro do *branch *de destino para apontar para o mesmo *commit *do *branch *de origem, evitando a criação de um novo *commit *de *merge*.
- **Semi-linear merge commit**
	- Mistura de rebase com merge.
- Simplex
- Full-Duplex

### Estratégia Recursive

A estratégia "recursive" é uma abordagem sofisticada que funciona da seguinte maneira:

1. **Ancestor Analysis**: O Git encontra o commit ancestral comum mais recente (common ancestor) das duas branches que estão sendo mescladas. Este commit é chamado de "merge base".
2. **Three-way Merge**: Com a base de merge identificada, o Git realiza uma mesclagem a três vias (three-way merge), onde ele compara as diferenças entre:
	- A base de merge (merge base)
	- O HEAD da branch atual (que você está mesclando para)
	- O HEAD da branch que está sendo mesclada (a branch de origem)
3. **Merge Commits**: Se não houver conflitos entre as alterações, o Git cria um novo commit de merge que une os históricos das duas branches.
4. **Conflict Resolution**: Se houver conflitos, o Git interrompe a mesclagem e marca os arquivos conflitantes. Você precisa resolver os conflitos manualmente e depois concluir o merge com um `git commit`.

### Exemplo Prático

Suponha que você esteja na branch `main` e deseja mesclar uma branch chamada `feature-branch`:

```shell
git checkout main
git merge feature-branch
```

O Git usará a estratégia de mesclagem recursive para integrar as mudanças de `feature-branch` na branch `main`.

### Estratégias de Mesclagem Alternativas

Embora "recursive" seja a estratégia padrão, Git suporta outras estratégias de mesclagem que podem ser usadas em situações específicas:

- **resolve**: Resolve um merge a dois pais, mas não tenta lidar com merges complexos.
- **octopus**: Usada para mesclar mais de duas branches. Útil para integrações de múltiplas branches ao mesmo tempo.
- **ours**: Este tipo de merge prefere as mudanças na branch atual e descarta as mudanças na branch sendo mesclada.
- **subtree**: Estrategia usada para merges de subprojetos.

Para especificar uma estratégia diferente, você pode usar a opção `-s`:

```shell
git merge -s resolve feature-branch
```

### Resumo

Em resumo, ao realizar um merge normal no Git, a estratégia padrão utilizada é a "recursive". Esta estratégia é robusta e eficiente para a maioria das situações de mesclagem, lidando bem com a complexidade das integrações e resolvendo conflitos quando necessário.

## Merge vs Rebase

O `git merge` e o `git rebase` são dois comandos usados para integrar mudanças de diferentes branches em um repositório Git, mas funcionam de maneiras diferentes e têm implicações distintas.

### Git Merge

O `git merge` combina o histórico de dois branches em um único branch, criando um novo commit de merge que tem dois pais (os últimos commits dos branches a serem mesclados).

**Como funciona:**

- **Fast-forward merge**: Se o branch de destino (por exemplo, `main`) não teve novos commits desde que o branch de origem foi criado, o merge simplesmente avança o ponteiro do branch de destino para o commit mais recente do branch de origem.
```plain text
git checkout main
git merge feature-branch

```
- **True merge**: Se ambos os branches têm novos commits, Git cria um novo commit de merge que une os dois históricos.
```plain text
git checkout main
git merge feature-branch

```

**Exemplo:**

```plain text
A---B---C (main)
     \\
      D---E (feature-branch)

```

Depois do merge:

```plain text
A---B---C---F (main)
     \\     /
      D---E (feature-branch)

```

O commit `F` é o commit de merge.

### Git Rebase

O `git rebase` pega os commits de um branch e os reaplica em cima de outro branch, criando novos commits. Isso reescreve o histórico de commits, resultando em um histórico linear.

**Como funciona:**

- **Rebase de branch em branch**: O branch de origem é reaplicado no topo do branch de destino.
Este comando move os commits do `feature-branch` para cima dos commits mais recentes do `main`.
```plain text
git checkout feature-branch
git rebase main

```

**Exemplo:**
Antes do rebase:

```plain text
A---B---C (main)
     \\
      D---E (feature-branch)

```

Depois do rebase:

```plain text
A---B---C---D'---E' (main)
                  (feature-branch)

```

Os commits `D'` e `E'` são novos commits que representam os commits `D` e `E` reaplicados.

### Comparação

- **Histórico**:
	- `git merge`: Preserva o histórico completo e a estrutura de ramificação.
	- `git rebase`: Reescreve o histórico, criando um histórico linear e mais limpo.
- **Commits**:
	- `git merge`: Cria um commit de merge.
	- `git rebase`: Não cria um commit de merge, reaplica commits.
- **Conflitos**:
	- `git merge`: Pode resultar em conflitos durante o merge.
	- `git rebase`: Pode resultar em conflitos durante o rebase, mas esses conflitos são resolvidos um por um para cada commit reaplicado.
- **Uso recomendado**:
	- `git merge`: Quando você deseja preservar o histórico completo e visualizar como os branches se juntaram.
	- `git rebase`: Quando você deseja manter um histórico linear e mais fácil de seguir.

### Exemplo prático:

- **Merge**:
```plain text
git checkout main
git merge feature-branch

```
    Preserva o histórico de branches.
- **Rebase**:
```plain text
git checkout feature-branch
git rebase main
git checkout main
git merge feature-branch

```
    Cria um histórico linear e sem commits de merge.

# GitLab

[https://www.youtube.com/watch?v=qP8kir2GUgo](https://www.youtube.com/watch?v=qP8kir2GUgo)

- Disponível em duas versões
	- Community (CE)
	- Enterprise (EE)
- Utiliza NGINX ou Apache como proxy
- Escrito em Ruby, roda em uma application server chamada puma
- Utiliza PostgreSQL para persistência de suas configurações e recursos

## Pipelines

![[Untitled 813.png]]

- As configurações de pipeline são feitas no arquivo `.gitlab-ci.yml` localizado na raiz do repositório
- É necessário garantir que existam “runners” disponíveis
	- Runners podem ser: 
		- SO (a serem especificados no arquivo)
		- Docker Images
	- Por padrão, a imagem Docker utilizada par um job, quando não especificado, será um container Ruby
	- Para especificar um container onde o job irá rodar, utiliza-se a tag `image`
- O usuário precisa ter o papel de Owner ou Maintainer do projeto
- Quando o arquivo for commitado para o repositório, o pipeline é iniciado
- Existe no GitLab uma interface chamada Pipeline Editor para facilitar a criação, testes, e outros recursos específicos para pipeline

```yaml
build-job:
  stage: build
  script:
    - echo "Hello, $GITLAB_USER_LOGIN!"

test-job1:
  stage: test
  script:
    - echo "This job tests something"

test-job2:
  stage: test
  script:
    - echo "This job tests something, but takes more time than test-job1."
    - echo "After the echo commands complete, it runs the sleep command for 20 seconds"
    - echo "which simulates a test that runs 20 seconds longer than test-job1"
    - sleep 20

deploy-prod:
  stage: deploy
  script:
    - echo "This job deploys something from the $CI_COMMIT_BRANCH branch."
  environment: production
```

- `stage`
	- Descrevem a execução sequencial dos trabalhos
	- stages com o mesmo nome serão executados em paralelo se existirem runners disponíveis
- `needs`
	- Especifica um pré-requisito, um job que deve estar finalizado para que a execução comece
```yaml
linux:build:
  stage: build
  script: echo "Building linux..."

mac:build:
  stage: build
  script: echo "Building mac..."

lint:
  stage: test
  needs: []
  script: echo "Linting..."

linux:rspec:
  stage: test
  needs: ["linux:build"]
  script: echo "Running rspec on linux..."
```
- `rules`
	- Podem especificar variações sobre quando rodar ou pular o stage
```yaml
job:
  script: echo "Hello, Rules!"
  rules:
    - if: $CI_MERGE_REQUEST_SOURCE_BRANCH_NAME =~ /^feature/ && $CI_MERGE_REQUEST_TARGET_BRANCH_NAME != $CI_DEFAULT_BRANCH
      when: never
    - if: $CI_MERGE_REQUEST_SOURCE_BRANCH_NAME =~ /^feature/
      when: manual
      allow_failure: true
    - if: $CI_MERGE_REQUEST_SOURCE_BRANCH_NAME
```
- `image`
	- Especifica a imagem que irá rodar o job
- `before_script`
	- Especifica os comandos que devem ser executados antes de iniciar o script
	- Útil para preparar a imagem docker para os testes que serão executados, como por exemplo, instalar dependências
- `variables`
	- Define variáveis que poderão ser referenciadas dentro do pipeline
	- Pode ser definida no contexto do pipeline ou dentro de um job específico
- Docker In docker (dind)
	- Para buildar uma imagem pelo pipeline, são necessárias duas imagens específicas:
		- Uma com as ferramentas CLI do docker, como por exemplo, `docker build`
		- Outra com o docker daemon
	- Para possibilitar que as duas imagens se comuniquem e tenham acesso uma a outra, utiliza-se a referência `services` e uma variável especial: `DOCKER_TLS_CERTDIR` que especifica onde a imagem do docker vai criar o certificado que possibilitará a comunicação entre as duas
- `services`
	- Especifica containeres auxiliares que deverão ser iniciados junto com a imagem principal, a fim de prover serviços
	- Por exemplo: Banco de dados
- `stages`
	- Definição dos estágios do pipeline
	- Jobs no mesmo estágio, poderão ser executados em paralelo
	- Os stages serão executados na sequência definida
	- Dentro do job, utiliza-se a tag `stage` para definir a qual estágio o job pertence

```yaml
variables:
        IMAGE_NAME: equinalha/cursogitlab
        IMAGE_TAG: python-app-1.0
stages:
    - test
    - build
		- deploy

run_tests:
    stage: test
    image: python:3.9-slim-buster
    before_script:
        - apt-get update && apt-get install make && echo ok
    script:
        - make test

build_image:
    stage: build
    image: docker:20.10.16
    services:
        - docker:20.10.16-dind
    variables:
        DOCKER_TLS_CERTDIR: "/certs"
    before_script:
        - docker login -u $REGISTRY_USER -p $REGISTRY_PASS
    script:
        - docker build -t $IMAGE_NAME:$IMAGE_TAG .
        - docker push $IMAGE_NAME:$IMAGE_TAG

deploy:
    stage: deploy
		# A Variável $SSH_KEY foi configurada no GitLab como sendo do tipo "file"
		# O que ele vai fazer e montar este arquivo e deixá-lo disponível para o container do estágio deploy
		# No entanto, as permissões padrão são muito abertas e o ssh dará um erro ao tentar utilizar a chave privada
		# Portanto no before_script, ajustamos as permissões do arquivo
    before_script:
        - chmod 400 $SSH_KEY
    script:
		# O comando de deploy será executado via ssh no servidor remoto
		# Nesta linha é especificado que o comando não peça confirmação nenhuma, faça a conexão e execute a linha de comando
		# que está entre aspas
		# Neste comando é feito o login no docker hub, listado os containeres que estejam em execução, excluídos, e então
		# feito novo docker run de forma que a imagem seja sempre puxada novamente e atualizada com base no docker hub
        - ssh -o StrictHostKeyChecking=no -i $SSH_KEY root@<server_IP_address> "
						docker login -u $REGISTRY_USER -p $REGISTRY_PASS &&
						docker ps -aq | xargs docker stop | xargs docker rm &&
						docker run -d -p 5000:5000 $IMAGE_NAME:$IMAGE_TAG"
```

- `workflow`
	- Controla quando o pipeline deverá ser executado
	- Por padrão, executa sempre que tiver um push ou commit
	- Porém, regras diferentes podem ser definidas
```yaml
workflow:
  rules:
    - if: $CI_COMMIT_MESSAGE =~ /-draft$/
      when: never
    - if: $CI_PIPELINE_SOURCE == "push"
```
- `include`
	- Importa outros arquivos de configuração de pipeline
	- pode ser:
		- `local`
		- `remote`

# Subversion (SVN)

> [!note] 🔥
> **SVN --> centralizado**
> **GIT --> distribuído**

- Os repositórios do Subversion (SVN) são** semelhantes aos do Git**, mas com várias diferenças em relação à arquitetura dos projetos.
- O SVN mantém um único servidor que contém todos os arquivos de controle de versão, e um número de clientes que usam arquivos a partir desse lugar central
- **Não é distribuído**
- Cada *referência*, ou instantâneo rotulado de um commit, em um projeto é organizado em subdiretórios específicos, como `trunk`, `branches` e `tags`
- O diretório `trunk` representa a última versão estável de um projeto.
- O trabalho de recursos ativos é desenvolvido em subdiretórios em `branches`.
- Quando um recurso é concluído, o diretório de recursos é mesclado em `trunk` e removido.
- Os projetos do Git também são armazenados em um único diretório. No entanto, o Git oculta os detalhes das referências armazenando-as em um diretório *.git* especial.
- Ao contrário do SVN, a estrutura de diretórios no Git permanece a mesma, mas o conteúdo dos arquivos é alterado de acordo com o branch que você possui.
- O SVN está configurado para pressupor que o histórico de um projeto nunca é alterado. O Git permite que você modifique os commits e as alterações anteriores usando ferramentas como o [`git rebase`](https://docs.github.com/pt/enterprise-server@3.11/get-started/using-git/about-git-rebase).
- quando um projeto atinge um ponto em que é considerado estável e pronto para a liberação, ele é frequentemente copiado para um diretório especial, conhecido como **branch**. 
-  Isso é feito para que o código possa ser congelado para testes finais, sem que alterações contínuas no tronco principal (trunk) afetem essa versão considerada estável.

# Resources

[https://learngitbranching.js.org/?locale=pt_BR](https://learngitbranching.js.org/?locale=pt_BR)

[https://dev.to/leandronsp/pt-br-fundamentos-do-git-um-guia-completo-2djh](https://dev.to/leandronsp/pt-br-fundamentos-do-git-um-guia-completo-2djh)

[[Git questions]]

> [!note]+ # Mapas Mentais
> ![[GIT.png]]
> 
> ![[GitLab.png]]
> 
> ![[Untitled 814.png]]