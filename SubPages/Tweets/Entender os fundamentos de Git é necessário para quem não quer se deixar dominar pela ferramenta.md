---
base: "[[Tweets.base]]"
Type: Thread
Created: 2022-12-04T09:02:00
Author: leandronsp
Tags:
  - Git
Tweet Link: https://twitter.com/leandronsp/status/1599255035405221888
---
> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Entender os fundamentos de Git é necessário para quem não quer se deixar dominar pela ferramenta. 

Nesta 🧵 vou tentar explicar as estruturas fundamentais do Git e como estas se relacionam com os comandos que usamos no dia-dia.
> [https://pbs.twimg.com/media/FjGnFzqXkAECKGY.png](https://pbs.twimg.com/media/FjGnFzqXkAECKGY.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Os principais componentes do Git são:

.git/objects
.git/refs
HEAD
> [https://pbs.twimg.com/media/FjGnj1zWIAIoTz9.png](https://pbs.twimg.com/media/FjGnj1zWIAIoTz9.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Começamos pelo Object database, que é basicamente onde o Git armazena todos os seus objetos.
> [https://pbs.twimg.com/media/FjGoIm7XgAYufbD.png](https://pbs.twimg.com/media/FjGoIm7XgAYufbD.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Mas que tipo de database é este? SQL? NoSQL?

Vamos primeiro persistir um objeto utilizando o comando `git hash-object`, que:

- permite input do STDIN ou arquivo normal
- retorna uma hash SHA-1
- persiste com a opção `-w`
> [https://pbs.twimg.com/media/FjGob7hXgAEPxqi.png](https://pbs.twimg.com/media/FjGob7hXgAEPxqi.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Podemos reparar que Git persistiu nosso objeto em .git/objects como era esperado, utilizando a hash que foi devolvida como "chave" de acesso
> [https://pbs.twimg.com/media/FjGor26XEAEWobU.png](https://pbs.twimg.com/media/FjGor26XEAEWobU.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Se temos a hash, conseguimos resgatar o valor original do objeto? 

Sim, com o comando `git cat-file`. 

Temos no Git, então, um database baseado em chave-valor, com suas chaves em formato SHA-1.
> [https://pbs.twimg.com/media/FjGo-eaWAAEl-YU.png](https://pbs.twimg.com/media/FjGo-eaWAAEl-YU.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
O comando `cat-file` permite passar a opção `-t` que devolve o tipo do objeto, que neste caso, é um blob.
> [https://pbs.twimg.com/media/FjGpeOnXoAIKAgP.jpg](https://pbs.twimg.com/media/FjGpeOnXoAIKAgP.jpg)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Uma vez com os blobs persistidos, como podemos agrupá-los, adicionar metadados e criar snapshots?

Precisamos promover estes blobs para um uma área de "Stage", com o comando `git update-index`
> [https://pbs.twimg.com/media/FjGp6z6WIAM03mo.png](https://pbs.twimg.com/media/FjGp6z6WIAM03mo.png)
> 
> [https://pbs.twimg.com/media/FjGqKphXgAAQsta.png](https://pbs.twimg.com/media/FjGqKphXgAAQsta.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Podemos adicionar quantos blobs quisermos ao índice utilizando o `update-index`. 

Mas como agrupá-los para que sejam promovidos? O Git permite criar uma "árvore" com esses blobs, através do comando `write-tree`.

Note que novos objetos foram criados, que tipos são esses objetos?
> [https://pbs.twimg.com/media/FjGqpvhWIAEV37F.png](https://pbs.twimg.com/media/FjGqpvhWIAEV37F.png)
> 
> [https://pbs.twimg.com/media/FjGqpv2WQAAPNfC.png](https://pbs.twimg.com/media/FjGqpv2WQAAPNfC.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Estes objetos são do tipo "tree", que servem para agrupar diferentes blobs e inclusive outras trees quando utilizada a opção `prefix`
> [https://pbs.twimg.com/media/FjGq-0wWQAAWi_F.png](https://pbs.twimg.com/media/FjGq-0wWQAAWi_F.png)
> 
> [https://pbs.twimg.com/media/FjGq-00XkAAVCnV.png](https://pbs.twimg.com/media/FjGq-00XkAAVCnV.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E se quisermos adicionar metadados a partir das trees, como por exemplo o autor do trabalho, a data e uma mensagem descritiva?

Sim, estamos falando do comando `git commit-tree`, que promove uma tree de modo a que esta possa ter metadados.
> [https://pbs.twimg.com/media/FjGrfvHXgAII7UC.png](https://pbs.twimg.com/media/FjGrfvHXgAII7UC.png)
> 
> [https://pbs.twimg.com/media/FjGrfvMWIAAKcEd.png](https://pbs.twimg.com/media/FjGrfvMWIAAKcEd.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Commits também são objetos, e portanto, possuem uma chave SHA-1 para representar cada commit.
> [https://pbs.twimg.com/media/FjGrss0XgAUs-Um.png](https://pbs.twimg.com/media/FjGrss0XgAUs-Um.png)
> 
> [https://pbs.twimg.com/media/FjGrstCWYAEEOPt.png](https://pbs.twimg.com/media/FjGrstCWYAEEOPt.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
É possível também criar commits com referência a outros commits (parents). 

Repare que o objeto commit tem referência para a tree e para o parent (outro commit criado a partir dele).
> [https://pbs.twimg.com/media/FjGr-GYWYAEGT4T.png](https://pbs.twimg.com/media/FjGr-GYWYAEGT4T.png)
> 
> [https://pbs.twimg.com/media/FjGr-GiWQAAo8cV.png](https://pbs.twimg.com/media/FjGr-GiWQAAo8cV.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Como percorrer toda a "rede" de commits a partir do último commit, indo pelos parents, trees até chegar nos blobs?

O comando `git log <sha1>` faz exatamente isso, percorrendo todo o grafo e trazendo tudo de acordo com a linha do tempo.
> [https://pbs.twimg.com/media/FjGsb5RWYAAduzc.png](https://pbs.twimg.com/media/FjGsb5RWYAAduzc.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Git é baseado em grafos.

Manipular objetos no Git é como manipular ponteiros em grafos. 

Blobs representam arquivos. Trees representam conjuntos de blobs e outras trees. Commits representam metadados com referência a trees e outros commits.
> [https://pbs.twimg.com/media/FjGtJQqXwAAX65B.png](https://pbs.twimg.com/media/FjGtJQqXwAAX65B.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Executar toda hora `git log <sha1>` não é eficiente pois temos de decorar as hashes. 

Mas Git traz uma facilidade para isto, que são referências para commits, que ficam em .git/refs. 

Através do comando `update-ref`, criamos referências que são basicamente commits "com nomes".
> [https://pbs.twimg.com/media/FjGt-O2WQAIux8x.png](https://pbs.twimg.com/media/FjGt-O2WQAIux8x.png)
> 
> [https://pbs.twimg.com/media/FjGt-PaX0AEnwqN.jpg](https://pbs.twimg.com/media/FjGt-PaX0AEnwqN.jpg)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Soa familiar? Estamos falando de branches.
> [https://pbs.twimg.com/media/FjGuN_8WYAUzKxi.png](https://pbs.twimg.com/media/FjGuN_8WYAUzKxi.png)
> 
> [https://pbs.twimg.com/media/FjGuOAbWIAE2CYf.png](https://pbs.twimg.com/media/FjGuOAbWIAE2CYf.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Mas o quê acontece se não passar argumento (sha-1) para o comando `git log`?

Como o Git sabe que a minha branch atual é a "main"?
> [https://pbs.twimg.com/media/FjGuhAjWQAMnfFt.png](https://pbs.twimg.com/media/FjGuhAjWQAMnfFt.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Acertou, é aqui que entra o tal do HEAD. 

Com o comando `git symbolic-ref` podemos mudar o ponteiro do HEAD, que é uma referência simbólica para a branch atual de trabalho.

O HEAD pode ser qualquer branch ou até mesmo um SHA-1 (no modo detached)
> [https://pbs.twimg.com/media/FjGvF-vXgAAjL33.png](https://pbs.twimg.com/media/FjGvF-vXgAAjL33.png)
> 
> [https://pbs.twimg.com/media/FjGvGBxWYAE9MdV.png](https://pbs.twimg.com/media/FjGvGBxWYAE9MdV.png)
> 
> [https://pbs.twimg.com/media/FjGvLMpXgAE51gE.png](https://pbs.twimg.com/media/FjGvLMpXgAE51gE.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Trocar o HEAD é uma simples chamada ao `symbolic-ref`. 

Neste exemplo, fico intercalando entre a branch "main" e branch "fix".
> [https://pbs.twimg.com/media/FjGvb1YXoAA2YMW.png](https://pbs.twimg.com/media/FjGvb1YXoAA2YMW.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Agora que sabemos que tudo em Git é manipulação de ponteiros, vamos associar este conhecimento com os comandos do dia-dia. 

Começando pelo `git add`, que basicamente é a junção do `hash-object` com `update-index`.
> [https://pbs.twimg.com/media/FjGv8JgWYAAt_Z5.jpg](https://pbs.twimg.com/media/FjGv8JgWYAAt_Z5.jpg)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
O `git commit` é basicamente o `write-tree` (uma vez que há objetos no index) seguido do `commit-tree`, que adiciona informações como autor, date e message.
> [https://pbs.twimg.com/media/FjGwUG4XoAEGNde.png](https://pbs.twimg.com/media/FjGwUG4XoAEGNde.png)
> 
> [https://pbs.twimg.com/media/FjGwUG_WAAAXWY5.png](https://pbs.twimg.com/media/FjGwUG_WAAAXWY5.png)
> 
> [https://pbs.twimg.com/media/FjGwUHDWQAA7O7Q.png](https://pbs.twimg.com/media/FjGwUHDWQAA7O7Q.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Já o `git checkout` é literalmente o `symbolic-ref`, que muda o ponteiro (branch) do HEAD.

Com algumas opções adicionais que trazem mais versatilidade.
> [https://pbs.twimg.com/media/FjGwoH9X0AAA9JC.png](https://pbs.twimg.com/media/FjGwoH9X0AAA9JC.png)
> 
> [https://pbs.twimg.com/media/FjGwoIeWYAE6SW9.png](https://pbs.twimg.com/media/FjGwoIeWYAE6SW9.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
O comando `git reset` permite mudar o ponteiro da branch, tal como o `update-ref`.

Sem a opção `--hard`, todos os arquivos que divergem ficam em stage a espera de novo commit.
> [https://pbs.twimg.com/media/FjGxWzMWQAE3TgH.png](https://pbs.twimg.com/media/FjGxWzMWQAE3TgH.png)
> 
> [https://pbs.twimg.com/media/FjGxWzxXEAE0uGC.png](https://pbs.twimg.com/media/FjGxWzxXEAE0uGC.png)
> 
> [https://pbs.twimg.com/media/FjGxZ_iX0AghGqD.png](https://pbs.twimg.com/media/FjGxZ_iX0AghGqD.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E o merge?

Bem, é super tranquilo entender. Supondo que temos uma branch main e outra "fix", onde fix está 1 commit à frente. 

O merge basicamente faz move a branch main para o mesmo commit da branch fix (fast-forward).
> [https://pbs.twimg.com/media/FjGx-J6X0AE6p5w.png](https://pbs.twimg.com/media/FjGx-J6X0AE6p5w.png)
> 
> [https://pbs.twimg.com/media/FjGx-LrWYAAZiYj.png](https://pbs.twimg.com/media/FjGx-LrWYAAZiYj.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E quando a main tem algum commit à frente da branch fix? Neste caso, não é possível fazer fast-forward.
> [https://pbs.twimg.com/media/FjGyd1LXwAASUI8.png](https://pbs.twimg.com/media/FjGyd1LXwAASUI8.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Mas o Git é bem inteligente e trata desta forma:

- Tira snapshot do parent em comum com ambas as branches
- Tira snapshot do commit da branch de destino
- Tira snapshot do commit da branch de origem

E, por fim, cria um commit adicional de "merge". Sim, é o "three-way" merge.
> [https://pbs.twimg.com/media/FjGyzLEWYAgjon_.png](https://pbs.twimg.com/media/FjGyzLEWYAgjon_.png)
> 
> [https://pbs.twimg.com/media/FjGyzLEWIAAvuOA.png](https://pbs.twimg.com/media/FjGyzLEWIAAvuOA.png)
> 
> [https://pbs.twimg.com/media/FjGyzLTXgAIFujX.png](https://pbs.twimg.com/media/FjGyzLTXgAIFujX.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Onde entra o cherry-pick? Com cherry-pick de um commit da branch main, o Git:

- move o ponteiro da branch fix
- aplica o commit da branch main como último commit na branch fix
> [https://pbs.twimg.com/media/FjG0ZXjWIAEyw5D.png](https://pbs.twimg.com/media/FjG0ZXjWIAEyw5D.png)
> 
> [https://pbs.twimg.com/media/FjG0ZXjXkAExPGg.png](https://pbs.twimg.com/media/FjG0ZXjXkAExPGg.png)
> 
> [https://pbs.twimg.com/media/FjG0ZX2WAAI2f99.png](https://pbs.twimg.com/media/FjG0ZX2WAAI2f99.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E quando queremos aplicar as mudanças por cima de outra branch?

Entra o rebase. 

Neste cenário, com rebase a partir da branch fix, basicamente:

- muda o ponteiro p/ o HEAD da main
- faz cherry-pick dos commits q sobraram
- por último muda ponteiro para o último do cherry-pick
> [https://pbs.twimg.com/media/FjGz29YXwAA2Mxs.png](https://pbs.twimg.com/media/FjGz29YXwAA2Mxs.png)
> 
> [https://pbs.twimg.com/media/FjGz29YXkAA4gqV.png](https://pbs.twimg.com/media/FjGz29YXkAA4gqV.png)
> 
> [https://pbs.twimg.com/media/FjGz29XX0AEfoFx.png](https://pbs.twimg.com/media/FjGz29XX0AEfoFx.png)
> 
> [https://pbs.twimg.com/media/FjGz29bXEAARczI.png](https://pbs.twimg.com/media/FjGz29bXEAARczI.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E as branches remote? 

Também são referências. 

O comando `git fetch` faz download da branch do server e sincroniza com uma branch "upstream" relacionada à tracking branch (local).
> [https://pbs.twimg.com/media/FjG0moVXgAE8yLE.png](https://pbs.twimg.com/media/FjG0moVXgAE8yLE.png)
> 
> [https://pbs.twimg.com/media/FjG1CHSXgAAHKf7.png](https://pbs.twimg.com/media/FjG1CHSXgAAHKf7.png)
> 
> [https://pbs.twimg.com/media/FjG1EfdWQAAqkyc.png](https://pbs.twimg.com/media/FjG1EfdWQAAqkyc.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Por serem branches, é possível fazer merge a partir das branches upstream com as locais.

Geralmente, por estarem sempre "atrás", merges com branches upstream são feitos no modo fast-forward.

O comando `git pull` facilita a vida, fazendo fetch + merge para nós.
> [https://pbs.twimg.com/media/FjG1Z4uXwAIy0J9.png](https://pbs.twimg.com/media/FjG1Z4uXwAIy0J9.png)
> 
> [https://pbs.twimg.com/media/FjG1Z5RX0AAcbqQ.png](https://pbs.twimg.com/media/FjG1Z5RX0AAcbqQ.png)
> 
> [https://pbs.twimg.com/media/FjG1Z5jXoAENgnk.png](https://pbs.twimg.com/media/FjG1Z5jXoAENgnk.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
"Okay, fiz meu trabalho e agora quero mandar de volta para o server. Como atualizo a branch upstream?"

Não precisa, o comando `git push`, além de atualizar o server, também sincroniza a branch tracking local com a upstream.
> [https://pbs.twimg.com/media/FjG1xosWQAAHhGr.png](https://pbs.twimg.com/media/FjG1xosWQAAHhGr.png)
> 
> [https://pbs.twimg.com/media/FjG1xosXkAIlYoh.png](https://pbs.twimg.com/media/FjG1xosXkAIlYoh.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Assim como branches, tags também são referências com "nome". 

Mas são imutáveis, ou seja, para mudar a referência de uma tag é preciso apagá-la e criar outra com mesmo nome.
> [https://pbs.twimg.com/media/FjG2LlaWIAEYsdp.png](https://pbs.twimg.com/media/FjG2LlaWIAEYsdp.png)
> 
> [https://pbs.twimg.com/media/FjG2LlZXoAA4kyt.png](https://pbs.twimg.com/media/FjG2LlZXoAA4kyt.png)

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
Como o [**@coproduto**](https://www.twitter.com/coproduto) destacou, nesta thread foram apresentados os comandos "plumbing", que foram os building blocks do Git, e como se relacionam com os comandos "porcelain", usados no dia-dia.

[**twitter.com/coproduto/stat…**](https://twitter.com/coproduto/status/1599260052783001600?s=20&t=sEGQ1uFh4Ky55Cik6YDcIA)
> > [!note] 📌
> > **testemunha de alonzo church **[***@coproduto:***](https://www.twitter.com/coproduto)
> Eu acho importante notar que o git tem dois conjuntos de comandos, conhecidos como "porcelain" e "plumbing". Os comandos "porcelain" são os que são usados no dia-a-dia, tipo add, commit, merge... E os "plumbing" são os relacionados com a visão do git como filesystem

> [!note] 📌
> **leandronsp **[***@leandronsp:***](https://www.twitter.com/leandronsp)
E pra quem tiver interesse, o próprio guia oficial do Git é bem completo, se ler os primeiros capítulos já cobre muita coisa boa para dominar mais o Git.

Com destaque ao capítulo 10 que fala dos "internals" que eu trouxe à thread.

[**git-scm.com/book/en/v2/Get…**](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)