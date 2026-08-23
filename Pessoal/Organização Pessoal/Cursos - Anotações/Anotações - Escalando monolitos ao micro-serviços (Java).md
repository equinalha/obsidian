---

---
# 1 - Tuning da Aplicação

## 1.1 - Servidor de aplicação - Tomcat

### 1.1.1 - Memória (Heap Size)

Por padrão a JVM do Tomcat executa com apenas 256MB de RAM (Heap Size). Existem dois parâmetros para subir o servidor com uma configuração personalizada de uso de memória: O mínimo e o máximo.

Para fins de performance, recomenda-se igualar o mínimo e o máximo, desta forma a JVM não perderá tempo fazendo escalação de memória.

Para uma máquina dedicada, recomenda-se utilizar de 50 a 75% do total de RAM da máquina

```java
// Exemplo para uso de 1GB
-Xms1024m -Xmx1024m
```

### 1.1.2 - Memória Perm Gen

Existe uma outra área de memória que pode ser otimizada também que é a Perm Gen space, local onde fica armazenado os binários e código fonte do Java

```java
-XX:MaxPermSize=192MB
```

### 1.1.3 - Modo servidor

```java
-server
```

### 1.1.4 - Parametrizar o Garbage Collector

## 1.2 - Aplicação

A maior latência encontra-se na camada de persistência dos dados, na maioria das vezes. O tempo de latência desta camada pode ser especificado da seguinte forma:

> [!tip] 💡
> T = Tacq + Treq + Texec + Tres + Tidle

Onde:

- **Tacq: **Tempo de aquisição de uma conexão com o banco. Inclui o processo de autenticação e handshake
- **Treq:** Tempo de montagem e envio da requisição ao banco
- **Texec:** Tempo de execução desta requisição no banco
- **Tres:** Tempo de envio da resposta
- **Tidle:** Tempo ocioso

### 1.2.1 - Tacq

Pode-se otimizar o tempo de aquisição de uma conexão com o uso de pool de conexões. Para chegar ao número ideal de conexões é necessário efetuar medições. Cada aplicação comporta-se de forma diferente. Uma ferramenta possível para isso é o **JProfiler**.

### 1.2.2 - Treq

> [!tip] 💡
> Casos em que exista um looping de ***inserts***, ***deletes*** e ***updates*** em uma aplicação, costumam disparar n requisições para o banco, tendo um custo elevado para o tempo de execução. O Hibernate oferece uma solução para isso com o uso do parâmetro **BATCH_SIZE.** Desta forma ele agrupa transações semelhantes, disparando apenas uma com o número de parâmetros especificados pela variável.

> [!tip] 💡
> Também é importante evitar o problema **select (n+1)** que ocorre quando há relação 1:n entre entidades e para um select do lado 1, dispara-se mais n selects para cada objeto relacionado.
> Este problema pode ser resolvido com o parâmetro fetchType = EAGER, porém é possível otimizar ainda mais.

> [!tip] 💡
> Pode-se utilizar o fetchType = LAZY porém na consulta JPSQL utilizar o parâmetro Join fetch
Otimiza-se ainda mais usando DTO, trazendo apenas os campos necessários para a consulta desejada.

### 1.2.3 - Texec

Usar:

- Índices
- Stored Procedures
- SQL Nativo

A filosofia básica neste caso é levar o processamento para perto de onde estão os dados.

### 1.2.4 - Cache

> [!tip] 💡
> O Entity Manager já é um cache de nível 1, ou seja, quando a mesma consulta é disparada mais de uma vez, ele não recorre mais ao banco pois já possui o resultado na memória.

> [!tip] 💡
> É possível utilizar um cache de segundo nível, ao nível do Entity Manager Factory. Este possibilita o armazenamento temporário de vários Entity Manager. Esta configuração pode ser habilitada via parâmetros do Hibernate.

Quanto mais próximo do banco, mais consistente é o Cache. Quanto mais próximo do usuário, mais performático.

# 2 - Usar Fila

Fila implica em processamento assíncrono. Cada vez que uma transação é cadastrada, ela fica em um banco específico (Redis, memcached) que apenas guarda os parâmetros da operação a ser realizada e libera o cliente.

Consumidores irão pegar o item da fila, executar a operação final no banco e por último atualizar seu estado.

O cliente terá que efetuar o monitoramento da fila para acompanhar o status da requisição.

# 3 - Scale up / Scale out

# 4 - Balanceadores de carga

Pode-se usar o apache ou nginx para isso. Aqui existe a questão da replicação de estado que pode ocorrer entre instâncias ou simplesmente ser removido para um cache a parte usando redis / memcached.

Por estado entenda-se o armazenamento da sessão.

# 5 - Microsserviços
