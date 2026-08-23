---

---
```bash
# NA rede default do docker, os containeres não
# podem comunicar-se entre si pelos nomes, apenas IPs.
# Para isso, deve-se criar uma rede
docker network create --driver bridge minha-rede
docker container run -it --name ubuntu --network minha-rede \
ubuntu


# Criar um container
docker container run -it <imagem>
docker container run --name <nome> <comando>

## OBS: o comando run sempre cria um novo container
# Iniciar um container criado anteriormente
docker container start <nome>

# Listar containeres
docker container ls
docker container ls -a

# Histórico de containeres executados
docker container ps
docker container ps -a

# Com montagem de volume
docker container run -p 8080:80 -v $(pwd)/:/usr/share/nginx/html nginx

# Rodando como Daemon (background)
docker container run -d --name ex-daemon-basic -p 8080:80 -v $(pwd)/html:/usr/share/nginx/html nginx

# Gerenciando container em background
# Uma vez que o container foi criado com o comando acima, pode-se usar:
docker container start <nome>
docker container stop <nome>
docker container restart <nome>

# Acessando logs
docker container logs <nome>

# Informações do container
docker container inspect <nome>

# Executar um comando no container
docker container exec <nome> <comando>

# Re-tagear imagens
docker image tag <tag atual> <novo tag>

## Dockerfile
FROM - Especifica a imagem que será utilizada. Ex: nginx:latest
RUN - Roda um comando dentro do container

# Construindo a imagem
docker image build -t <tag da imagem> . #assumindo que o Dockerfile está no dir local

# Rede
## Existem três drivers de rede: none, bridge e host
## O padrão é o modo bridge, que monta um segmento de rede separado da rede física
## O modo host compartilha a mesma rede da máquina host
docker network ls
docker network inspect <nome da rede>
docker container run --net <nome da rede> <nome do container> <comando do linux>
docker network create --driver <driver> <nome_da_rede> # Cria uma nova rede, com uma nova faixa de IP.
docker network connect <nome da rede> <nome do container> # É possível um container estar conectado a mais de uma rede, assim como nenhuma, através do driver none
docker network disconnect <nome da rede> <nome do container>

# Exemplos:
docker container run --rm --net none alpine ash -c "ifconfig"
docker network inspect bridge
docker container exec -t container2 ping 172.17.0.2

# Docker Compose
## Utilizado para orquestrar vários containeres representando um ambiente
## Ex: Backend, frontend, DB
# Utilizar arquivo yml
# Exemplo:
# docker-compose.yml
version: '3'
services:
  db:
    image: mongo:3.4
  backend:
    image: node:8.1
    volumes:
      - ./backend:/backend
    ports:
      - 3000:3000
    command: bash -c "cd /backend && npm i && node app"
  frontend:
    image: nginx:1.13
    volumes:
      - ./frontend:/usr/share/nginx/html/
    ports:
      - 80:80

# Comando para subir o ambiente:
docker-compose up

# Acompanhando os logs:
docker-compose logs -f -t (<nome do serviço>)

# Escalando
docker-compose up -d --scale <serviço>=<num de instâncias>

# Override
> basta criar um arquivo docker-compose.override.yml

## Tipos de volumes:
# Bind - Equivalente ao mount do linux. Apenas linka uma pasta na outra
docker container run -v /home/user/teste/:/app ubuntu
# Volume - Cria um volume gerenciado pelo docker em /var/lib/docker/<hash>/volumes
docker container run -v /app ubuntu
# Volume nomeado - Cria um volume de nome definido, gerenciado pelo docker
docker volume create my-vol
docker container run -v my-vol:/app ubuntu
```

```bash
sudo docker container run -p 3000:3000 -e DB_PASSWD=ZEBKIRmC3jvwIIvF -e DB_URL=sandbox.aqyvv.gcp.mongodb.net -e DB_USER=obrasAgilUser -e DB_DB=obrasAgil -e AUTH_SECRET=2AebZeN*aE0u%IAeBM@gw6GEgtwhVp -e BCRYPT_SALT=10 -e TOKEN_EXPIRES=30m  -v /media/windows/DATA/DEV/TKBS/slidesTemplates/:/usr/src/tkbsBackend/src/public/templates -v /media/windows/DATA/DEV/TKBS/slidesImages/:/usr/src/tkbsBackend/src/public/images equinalha/tkbsbackend:0.3
```
