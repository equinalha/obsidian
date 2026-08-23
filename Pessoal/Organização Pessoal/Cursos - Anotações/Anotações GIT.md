---

---
Comandos:

Configurações básicas

```plain text
Iniciando um repositório na pasta atual:
	git init

Configurações de usuário:
	git config --global user.name
	git config --global user.email
	git config --global core.editor

Visualizar configurações
	git config --list
	git config user.name
	git config user.email
	git config core.editor

Estado atual do repositório
	git status

	Os estados são:
		Untracked - Existem arquivos no repositório, mas não foram adicionados ao git, portanto não têm sua versão controlada
		Unmodified - O arquivo está no repositório, no git, mas não foi modificado
		Modified - Arquivo modificado mas não "commitado"
		Staged - Após o commit

Controle de versões
	git add <nome do arquivo>
	git commit
	git log
	git shortlog
	git shortlog -sn
	git log --graph
	git log --author "<nome>"
	git show <hash do commit> - Mostra detalhadamente as alterações do respectivo commit

	git diff - Mostra as mudanças que ocorreram após uma modificação
	git diff --name-only

Desfazendo coisas
	git chechout <arquivo> -> Arquivo modificado, não está em staged ainda
	git reset HEAD <arquivo> -> Para arquivos já em staged

	git reset --soft <Hash do commit anterior ao que vai ser desfeito> -> desfaz o commit, mas deixa o arquivo em staged, pronto para um novo commit
	git reset --mixed <Hash do commit anterior ao que vai ser desfeito> -> desfaz o commit e o staged, retorna o arquivo para modified
	git reset --hard <Hash do commit anterior ao que vai ser desfeito> -> desfaz todas as alterações, volta ao estado antes da mudança

Trabalhando com repositório

	geração da chave SSH
		ssh-keygen -t rsa -b 4096 -C "eduardoquinalha@gmail.com"

	-> Adicionar a chave pública no repositório

	Adicionando um repositório remoto
		git remote add origin <https://github.com/EdQnl/Curso-Github.git> 		- HTTPS
		git remote add origin <git@github.com:EdQnl/Curso-Github.git> 			- SSH

			-> origin na verdade pode ser qualquer nome. É apenas um apelido para o repositório desejado

		git push -u <remoto> <branch>
			Exemplo: git push -u origin master

		A cada novo commit, deve ser feito este comando para replicar as alterações no repositório remoto

	Clonando
		Em uma pasta vazia

			git clone <repositório>

			Se tiver problemas com certificado SSL

			GIT_SSL_NO_VERIFY=true git clone <repositório>
Branches
	São úteis para que comits de pessoas trabalhando em paralelo não entrem em conflitos
	Também pode ser útil para realizar um teste que pode ou não dar certo, no final ser descartado sem alterar a versão principal

	Criando um branch
		git checkout -b <nome_do_branch>

	Navegando entre branches
		git checkout <nome_do_branch>

	Deletando um branch
		git branch -D <nome_do_branch>

	Exibindo branches
		git branch

	Unindo Branches
		Merge
			Junta duas ramificações em uma só
			Não destrutiva
							(HotFix)
							 - C4 -
						   /       \\
			c1 <- c2 <- c3 <- C5 <- C6 (Merge)
							(Master)

		Rebase
			Utilizado em testes. Se deu certo, faz um rebase e este nó volta ao ramo principal, tornando-se a versão oficial.
			Master e o branch passam a ser o mesmo commit
							(experiment)
							 - C4 - X
						   /
			c1 <- c2 <- c3 <- C5 <- C4' (Rebase): (experiment) = (master)
							(Master)

	Avançado
		.gitignore - Arquivo em que podemos pedir ao git que ignore determinados arquivos. Pode-se utilizar coringas

		git stash - Guarda as alterações atuais em um nó separado (stash), voltando o nó (branch) atual para o estado anterior. Permitindo que vc faça 				outra alteração ou commit, guardando a anterior para depois
		git stash apply - retorna a alteração guardada com o git stash

		Alias:
			git config --global alias.<nome_do_alias> <comando>

			Exemplo:	git config --global alias.s status

		Tags:

		git revert <hash do commit> - Faz um novo comit, desfazendo o commit desejado, porém sem apagar este do histórico

```
