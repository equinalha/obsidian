---
base: "[[Tweets.base]]"
Type: Thread
Created: 2022-12-12T15:00:00
Author: Marajá dos Legados
Tags:
  - Webdev
Tweet Link: https://twitter.com/rponte/status/1602319683784695808
---
> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
vc sabe quais são os 3 pilares para escalar aplicações web?

existem 3 pilares para escalar qualquer aplicação web, independente de tecnologias, eles são:

1. Cache
2. Processamento Assincrono
3. Balanceamento de Carga
> [https://pbs.twimg.com/media/FjyKtFSXkAAJuwt.jpg](https://pbs.twimg.com/media/FjyKtFSXkAAJuwt.jpg)

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
1. Cache

cache vai permitir responder as requisições mais rapidamente, tirar carga do banco de dados e serviços externos, e melhorar throughput de leitura;

ao retirar carga de leitura do banco vc libera recursos para o banco processar cargas de escrita e também leitura.
> [https://pbs.twimg.com/media/FjyTbUXX0AI2iFh.jpg](https://pbs.twimg.com/media/FjyTbUXX0AI2iFh.jpg)

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
2. Processamento Assincrono

operações pesadas e custosas são geralmente os maiores gargalos, por isso postergar a execução p/ um momento mais oportuno e controlado eh o indicado;

usar fila de msgs ou job em background eh o caminho para processar no ritmo que sua app aguenta
> [https://pbs.twimg.com/media/FjyMVIbXgAIH6zd.jpg](https://pbs.twimg.com/media/FjyMVIbXgAIH6zd.jpg)

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
3. Balanceamento de Carga

a idéia aqui eh aumentar o número de maquinas para aumentar a escala, para isso colocamos uma máquina de Load Balancer na frente para distribuir a carga entre as máquinas;

precisa de mais throughut? basta adicionar mais máquinas
> [https://pbs.twimg.com/media/FjyMn1HWYAAgbDu.png](https://pbs.twimg.com/media/FjyMn1HWYAAgbDu.png)
> 
> [https://pbs.twimg.com/media/FjyRdyPXgAMiMYW.png](https://pbs.twimg.com/media/FjyRdyPXgAMiMYW.png)

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
cada um desses pilares traz consigo desafios e tradeoffs

simplesmente achar que colocar um cache com Redis ou fila com Kafka na frente da sua aplicação vai melhorar as coisas sem entender o que vc perde com isso eh perigoso

lembre-se: performance e escala não vem de graça
> [https://pbs.twimg.com/media/FjyPbzmWYAEyVMd.png](https://pbs.twimg.com/media/FjyPbzmWYAEyVMd.png)
> 
> [https://pbs.twimg.com/media/FjyRw_XWAAABAg3.png](https://pbs.twimg.com/media/FjyRw_XWAAABAg3.png)

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
"tarefas de casa"

antes de correr p/ estes 3 pilares e adota-los na sua arquitetura as chances são de q vc tem muito trabalho p/ fazer, como:

- melhorar seu código
- otimizar as queries do banco
- configurar pool de conexões
- configurar timeouts
- remover estado da app
- etc

> [!note] 📌
> **Marajá dos Legados **[***@rponte:***](https://www.twitter.com/rponte)
se quiser entender de forma DIDÁTICA sobre:

- esses 3 pilares e suas motivações de uso;
- alguns dos desafios e tradeoffs;
- e as tais "tarefas de casa"; 

te convido a assistir essa talk sobre "Arquitetura Web" no canal do youtube da [**@ZupInnovation**](https://www.twitter.com/ZupInnovation) :

[**youtu.be/uoLTYZL6qWo?li…**](https://youtu.be/uoLTYZL6qWo?list=PLHMMERsvy9EyWQPru4SrJAYHEGKfkjRgP&t=586)