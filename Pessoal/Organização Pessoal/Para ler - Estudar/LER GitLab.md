---

---
[https://blog.4linux.com.br/ci-cd-com-gitlab/](https://blog.4linux.com.br/ci-cd-com-gitlab/)

![[CI_CD_com_Gitlab-3800x1445_c.png]]

### O que é o Gitlab?

O Gitlab é uma ferramenta que agrega diversas funcionalidades, mas, primordialmente, é um gerenciador de repositório baseado em Git, assim como o Github. Hoje em dia, além da funcionalidade citada, ele também conecta diversas ferramentas do mundo DevOps, assim como conceitos de CI/CD e até mesmo Kubernetes.

### Como usar o CI/CD do Gitlab?

Preferencialmente, devemos ter um arquivo no nosso repositório com o nome “.gitlab-ci.yml”. Esse é o nome padrão do arquivo que será utilizado nas pipelines do Gitlab, mas você pode configurar para ter outro nome.

- Para que possamos denominar o arquivo de pipeline com outro nome, basta acessar as configurações do seu repositório

![[cicd-1.png]]

- Selecione a opção CI/CD das configurações
	Clique em expandir a opção Pipelines Gerais
![[cicd-2.png]]

![[cicd-3.png]]

- Configure o caminho ou nome do seu arquivo yml da pipeline
	Após ter criado seu arquivo com extensão .yml, iremos configurar uma simples pipeline só para entender o processo que o Gitlab utiliza. 😀
![[cicd-4.png]]

### Como criar o arquivo para a pipeline

Você pode utilizar seu editor de preferência, mas o Gitlab fornece uma IDE de desenvolvimento web ^^, basta acessar o arquivo que deseja editar e clicar em IDE Web

Agora podemos finalmente criar o código, conforme o exemplo abaixo:

![[cicd-5.png]]

```plain text
build-job:
    stage: build
    script:
        - echo "Ola, $GITLAB_USER_LOGIN!"

test-job:
    stage: test
    script:
        - echo "Esse é um teste"


deploy-prod:
    stage: deploy
    script:
        - echo "Este deploy esta sendo feito na branch $CI_COMMIT_BRANCH"

```

Basicamente, este código indica os estágios de desenvolvimento que iremos utilizar. No Gitlab, podemos ter 4 nomes para os estágios, sendo eles:

1. build
2. test
3. deploy
4. .post

Em cada um dos 3 estágios principais, utilizamos um script, que nada mais é do que um shell rodando por trás. Claro que utilizamos exemplos simples para mostrar a funcionalidade.
 Além disto, podemos ver variáveis que não foram declaradas neste arquivo, que são variáveis padrão do Gitlab encontradas na documentação: [variaveis ](https://docs.gitlab.com/ee/ci/variables/predefined_variables.html)sendo as mostradas

5. $GITLAB_USER_LOGIN = Nome do usuário que esta rodando o job
6. $CI_COMMIT_BRANCH = Nome da branch que o job esta rodando

Com o código acima, ao clicarmos em Commit, o Gitlab irá automaticamente iniciar a tentativa de rodar este job.

Insira a mensagem de Commit e o deploy será iniciado automaticamente

![[cicd-6.png]]

Agora, ao retornar ao menu do projeto e clicar em CI/CD pipelines, você será guiado até o histórico das pipelines, onde a pipeline inicial terá seu status de sucesso ou falha

Ao acessar os jobs, é possível ver quais passos falharam ou passaram

Ao clicar em algum dos passos, podemos ver os logs da execução

E com isto finalizamos a utilização da pipeline no Gitlab. 🙂