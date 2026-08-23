---
base: "[[Concursos.base]]"
Verification: unverified
Tags: []
Last edited time: 2024-11-12T07:48:00
Owner:
  - Eduardo Quinalha
---
[https://www.youtube.com/watch?v=pg19Z8LL06w](https://www.youtube.com/watch?v=pg19Z8LL06w)

# Docker vs Containeres Linux Tradicionais

- <u>O Docker não fornece as mesmas funcionalidades parecidas com UNIX que os containers Linux tradicionais oferecem.</u> Isso inclui a capacidade de usar processos como cron ou syslog dentro do container, junto à aplicação.
- <u>O Docker também tem algumas limitações em questões como a limpeza de processos netos (</u><u>*grandchild*</u><u>) após o encerramento dos processos filhos (</u><u>*child*</u><u>), algo que é processado de forma natural nos containers Linux tradicionais</u>.

# Principais Comandos

- `docker ps` lista os containeres em execução, equivalente a `docker container ls`
- `docker run -p<local>:<container> <imagem>` → Para memorizar `-p LC`
	- Run combina dois comandos: pull e start
- `attach` → Attach local standard input, output, and error streams to a running container
- `build`  →  Build an image from a Dockerfile
- `commit` → **Create a new image from a container's changes**
- `cp` → Copy files/folders between a container and the local filesystem
- `create` → Create a new container
- `diff` → **Inspect changes to files or directories on a container's filesystem**
- `export`/`import` → **exporta / importa containeres para arquivos .tar. Exporta somente o sistema de arquivos, sem os metadados**
- `history` → **Detalha as camadas do container**
- `inspect` → Return low-level information on Docker objects
- `port` → List port mappings or a specific mapping for the container
- `rmi` → Remove one or more images
- `save`/`load` → **Exporta imagens docker, junto com metadados e permite a recriação da imagem**
- `top` → **Display the running processes of a container**
- `update` → Update configuration of one or more containers
- `stats` → **Exibe informação sobre o consumo de recursos de um ou vários containeres em real time**

# Volumes

- Criando um volume:
	- `docker volume create ``**my-volume**`
	- Na prática, não precisa executar o comando de criação de volume. No comando docker run, se for especificado um volume, o docker irá criá-lo automaticamente.
- Usando:
	- `docker run -dp 127.0.0.1:3000:3000 ``**--mount**`` type=volume,src=``**my-volume**``,target=/etc/todos getting-started` ou
	- `docker run -dp 127.0.0.1:3000:3000 ``**-v my-volume:**``/etc/todos getting-started`
- É possível obter detalhes sobre o volume, inclusive o local de armazenamento, utilizando o comando `docker volume inspect`

```json
docker volume inspect todo-db
[
    {
        "CreatedAt": "2019-09-26T02:18:36Z",
        "Driver": "local",
        "Labels": {},
        "Mountpoint": "/var/lib/docker/volumes/my-volume/_data",
        "Name": "my-volume",
        "Options": {},
        "Scope": "local"
    }
]
```

## Bind Mounts

- Ao invés de criar um volume, pode-se também especificar um diretório local no filesystem da máquina host para que seja utilizado como persistência para o container
- `docker run (…) --``**mount**`` type=bind,src=/path/to/data,target=/usr/local/data (…)`

```bash
docker run -dp 127.0.0.1:3000:3000 \
    -w /app --mount type=bind,src="$(pwd)",target=/app \
    node:18-alpine \
    sh -c "yarn install && yarn run dev"
```

## tmpfs Mounts

- Monta uma unidade de armazenamento temporária na **memória** do host
- Disponível somente para hosts linux
- Não é persistente
- Não pode ser compartilhada entre containeres

# Networking

- Por padrão contineres rodam em isolamento e não conseguem se comunicar com outros containeres na mesma máquina host.
- Para que eles possam se comunicar, é necessário criar uma rede docker e colocar os dois containers na mesma rede
- Métodos
	- Asoociar o container a uma rede ao criá-lo / iniciá-lo
	- Connecar um container em execução a uma rede
- Criando a rede: `docker network create ``**my-network**`
- Rodando um conainer na rede criada

```bash
docker run -d \
     --network my-network --network-alias mysql \
     -v my-volume:/var/lib/mysql \
     mysql:8.0
```

- Ou de forma mais simples: `docker run -it --network ``**my-network**`` nicolaka/netshoot`
- Uma vez que dois containeres estejam na mesma rede, eles podem se referenciar um ao outro pelo **network-alias**. O DNS irá traduzir automaticamente para o endereço IP correspondente de cada um
- Docker manipula regas do iptables no linux
	- Quando se especifica o atributo `-p` ou `--publish`, o docker cria uma regra de firewall no host, mapeando a porta do container para uma porta na máquina host
	- exemplos

| `-p 8080:80` | Map TCP port 80 in the container to port `8080` on the Docker host. |
| --- | --- |
| `-p 192.168.1.100:8080:80` | Map TCP port 80 in the container to port `8080` on the Docker host for connections to host IP `192.168.1.100`. |
| `-p 8080:80/udp` | Map UDP port 80 in the container to port `8080` on the Docker host. |
| `-p 8080:80/tcp -p 8080:80/udp` | Map TCP port 80 in the container to TCP port `8080` on the Docker host, and map UDP port 80 in the container to UDP port `8080` on the Docker host. |
- É possível conectar um container existente em uma rede diferente (adicional) usando o comando `docker network connect` e `—ip` ou `—ip6`. Desta forma é possível ter o container se comunicando com duas (ou mais) redes simultaneamente
- `--hostname` → Por padrão, o docker usa o ID do container como hostname. Para especificar um hostname diferente, pode-se utilizar este parâmetro
- `/etc/hosts` → Hosts customizados adicionados no /etc/hosts não são migrados para o container

## Network Drivers

- **bridge** 
	- Default
	- Usando quando o container precisa se comunicar com outros **no mesmo host**. Containeres em redes diferentes do tipo bridge, não podem se comunicar diretamente.
	- Containeres criados sem especificação de rede conectam-se a uma bridge default. Estes containeres poderão comunicar-se apenas via endereço IP
		- A menos que seja especificado a opção `--link` nos dois containeres que desejam comunicar-se
	- Bridges especificadas pelo usuário possuem uma **resolução DNS automática **entre containeres
- **host**
	- Remove o isolamento de rede entre o container e o host (funcionam como se fossem a mesma máquina, a nível de rede)
	- O container utiliza a rede do host diretamente e **compartilha o mesmo endereço IP**
	- `docker run -d --network=host nginx`
- **overlay**
	- Conecta múltiplos Docker Daemons e habilita os serviços Swarm entre eles
	- Não há necessidade de roteamento a nível de sistema operacional
	- É necessário liberar portas de firewall para comunicação entre os nós Docker:
		- TCP port 2377 for cluster management communications
		- TCP and UDP port 7946 for communication among nodes
		- UDP port 4789 for overlay network traffic
	- Também é necessário iniciar o Docker Daemon no modo swarm: `docker swarm init` ou integrá-lo em um swarm existente:` docker swarm join`
	- Para criar uma rede no modo overlay: `docker network create -d overlay my-overlay`
- **ipvlan**
	- Permite comunicação direta do container com a mesma rede IP do host
	- Não é necessário bridge ou NAT translation
	- Requer suporte do kernel
```bash
docker network create -d ipvlan \
    --subnet=192.168.1.0/24 \
    --gateway=192.168.1.1 \
    -o ipvlan_mode=l2 \
    -o parent=eth0 db_net
```
- **macvlan**
	- Permite atribuir um MAC Address para o container, fazendo parecer que ele está fisicamente conectado à rede
	- Permitem que os containeres se comuniquem diretamente com dispositivos de rede, mas não permite que comuniquem-se diretamente entre si, sem passar pela interface e necessitar de regras de roteamento
- **none**
	- Isolamento total do container

# Docker Compose

```yaml
services:
  app:
    image: node:18-alpine
    command: sh -c "yarn install && yarn run dev"
    ports:
      - 127.0.0.1:3000:3000
    working_dir: /app
    volumes:
      - ./:/app
    environment:
      MYSQL_HOST: mysql
      MYSQL_USER: root
      MYSQL_PASSWORD: secret
      MYSQL_DB: todos

  mysql:
    image: mysql:8.0
    volumes:
      - todo-mysql-data:/var/lib/mysql
    environment:
      MYSQL_ROOT_PASSWORD: secret
      MYSQL_DATABASE: todos

volumes:
  todo-mysql-data:
```

# Multi-stage Build

- Em um Dockerfile podem ser especificados estágios para a construção do aplicativo

```docker
# syntax=docker/dockerfile:1
FROM maven AS build
WORKDIR /app
COPY . .
RUN mvn package

FROM tomcat
COPY --from=build /app/target/file.war /usr/local/tomcat/webapps
```

# ENTRYPOINT vs CMD

- `ENTRYPOINT` é o comando que será executado sempre que o container executar
- Caso não especificado, o **default** é `**/bin/sh -c**`
- `CMD` é o argumento passado para o `ENTRYPOINT`
- Na linha de comando, tudo que vem após o nome da imagem é o CMD
- Quando se executa, por exemplo: `docker run -i -t ubuntu bash`
	- O que está sendo executado de verdade é `**/bin/sh -c bash**`
- Quando se especifica algo diferente em `ENTRYPOINT `por exemplo `java -jar /app.jar` este comando será executado sem um wrap de shell
- Pode ser vantajoso, principalmente em containeres que executam aplicações java

[[Docker Network]]

# Armazenamento

[https://stack.desenvolvedor.expert/appendix/docker/armazenamento.html](https://stack.desenvolvedor.expert/appendix/docker/armazenamento.html)

- Backend de armazenamento é a parte da solução do Docker que cuida do gerenciamento dos dados.
- Existem várias possibilidades, porém o mais utilizado é o AUFS
	- É responsável por gerenciar múltiplos diretórios, empilhá-los uns sobre os outros e fornecer uma única e unificada visão, como se todos juntos fossem apenas um diretório.
	- Esse único diretório é utilizado para apresentar o container e funciona como se fosse um único sistema de arquivos comum. 
	- Cada diretório usado na pilha corresponde a uma camada. 
	- Unifica e proporciona a reutilização entre containeres
	- Com exceção da pasta (camada) correspondente ao container, todas as outras são montadas com permissão de somente leitura, caso contrário as mudanças de um container poderiam interferir em outro.
	- Caso seja necessário modificar um arquivo nas camadas (pastas) referentes às imagens, se utiliza a tecnologia [Copy-on-write](https://en.wikipedia.org/wiki/Copy-on-write) (CoW), responsável por copiar o arquivo para a pasta (camada) do container e fazer todas as modificações nesse nível. 
![[image 126.png]]
	- No caso da remoção, o arquivo da camada superior é marcado como whiteout file, viabilizando a visualização do arquivo de camadas inferiores.
