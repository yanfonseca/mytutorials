## Docker 

### Comandos básicos

    docker --help

    docker image list

    docker image pull nome_da_imagem

    docker image inspect nome_da_imagem

### Parâmetros usados para execução de um contêiner

    docker container run -d -it python

| Parâmetros |  Função   |
|------------|-----------|
|   -d       | Execução em background |
| -i         | Modo interativo |
| -t         |Aloca pseudo TTY|
|  -rm       | Remove o conteúdo automaticamente após sua finalização|
| -name      | Nomear contêiner|
| -v         | Mapeia volume   |
|-p          | Mapeia porta   |
| -m         | Limita o uso de memória RAM|
| -c         | Balancear o uso da CPU. O maior peso é 1024|

* Mapepamento de porta

        docker container run -p host:container nome_da_imagem

* Gerenciamento da RAM e CPU

        docker container run -m 512M nome_da_imagem
        docker container run -c 512 nome_da_imagem

### Lista de contêineres
    
    docker container ls -a

| Parâmetros |  Função   |
|------------|-----------|
|   -a       | Lista todos os contêineres, em uso ou não |
| -l        | Lista últimos contêineres|
| -n         |Lista os últimos N contêineres, em uso ou não|
|  -q       | Lista os ids dos contêineres|

### Iniciar e parar um contêiner

* Se usar a flag -i no start, vai direto para o modo interativo.

      docker container start nome_do_container

      docker container stop nome_do_container

### Como criar imagens?

1. É possível criar uma imagem a partir de um contêiner que foi modificado. Depois das modificações basta parar o contêiner e criar a imagem.

    * Parar o contêiner
        
            docker container stop nome_do_container

    * Salvar o contêiner

            docker container commit nome_do_container nome_da_imagem:versao_da_imagem

2. Através do Dockerfile

* Criar uma pasta

* Criar um arquivo chamado Dockerfile. Dentro do arquivo escrever as instruções para a criação da imagem:

```
FROM ubuntu:16.04
RUN apt-get update && apt-get install nginx -y
COPY file_copy_to_container /tmp/file_copy_to_container
CMD Bash
```
* o que significa?
    
    FROM - Através da imagem ubuntu:16.04
    
    RUN  - aplique os comandos, equivalente a digitar no terminal
    
    COPY - Copie dados de um diretório ou copie uma pasta para /tmp
    
    CMD  - No modo iterativo, por padrão, abrirá o bash

* O -t é o parâmetro para informar o nome da imagem:

        docker image build -t nome_da_imagem:versao_da_imagem
    
### Armazenamento no Docker

* Mapeamento de pasta específica do host que pode ser compartilhada com contêiner. 
Lembrando que a regra host:container é válida aqui.

    docker container run -v /var/lib/container1:/var ubuntu

* Volume em um contêiner que vai ser consumido por outros contêiners(contêiner especial).

        docker create -v /dbdata --name dbdata postgres /bin/true

    Para consumir o volume do contatêiner acima:

        docker container run -d --volumes-from dbdata --name db2 postgres

    Dessa forma, o contêiner db2 acessará a pasta dbdata do contêiner dbdata, 
    o que facilita na portabilidade dos contêineres já que existe independência 
    em relação ao host.

* Na versão 1.9 foi criada a possibilidade de criar volumes isolados de 
contêineres e que podem ser consumidos por quaisquer contêineres. Essa forma de compartilhamento de volumes é a recomendada.

    docker volume create --name dbdata

    * É necessário associar uma pasta de dentro do contêiner com o volume isolado. 

    docker container run -d -v dbdata:/var/lib/data postgres

### Rede no Docker

1. Mostra as criadas

        docker network ls

1. Bridge - Rede padrão para os contêineres. Cria uma interface que faz a ponte entre 
    docker0 do docker host. Recebe o endereço de ip automaticamente. 
    Se o docker host tiver acesso a a internet, os contêineres também terão.

1. none - Serve para isolar o contêiner para comunicações externas e não recebe 
interface para comunicação externa e somente a interface com localhost. É uma rede usada para 
contêineres que manipulam arquivos e não precisam enviá-los para outro local. Por exemplo, 
o contêiner de back up que através do volume de contêiner de banco de dados faz o dump.

    
1. host

* Redes que podem ser criadas usando drivers:

    * Driver Bridge. Já tem o serviço DNS do docker.

            docker network create --driver bridge isolated_nw
        
            docker network list
    
    Contêineres de um rede não pode acessar outro contêiner de outra rede, para isso é necessário
    expor postas no docker host.

    Para descobrir contêineres associados a uma rede:

      docker network inspect isolated_nw

    * Driver Overlay

        Permite a comunicação entre hosts docker.

### Docker em diferentes ambientes

1.  Docker machine: https://docs.docker.com/machine/

    * Responsável pela gerência distribuída, permite instalar e gerenciar docker hosts.

1. Docker é dividido em Docker Host e Docker Client:
        * o primeiro roda em backrgroud e o segundo é resonsável por recebeber comandos que gerenciam o Docker Host.

1. É necessário usar dos drivers: https://docs.docker.com/machine/drivers/

#### Comandos

Lembrando que é necessário instalar o Docker Machine antes caso contrário o comando não será encontrado.

    docker-machine create -driver=nome_do_driver nome_do_ambiente

### Docker compose

* Simplifica a execução de múltiplos contêineres.
* Cada contêiners é considerado um serviço.
* Também é possível especificar volumes, redes para os serviços.
* O arquivo de definição do Docker Compose é o local onde é espeficiado todo o ambiente, 
os serviços, o volume e a rede. 
* Esse arquivo tem o formato YAML e docker-compose.yml é seu nome padrão.

#### Como é o arquivo docker-compose.yml?

* No arquivo a identação é importante
* Cada linha é definida como uma chave, valor ou lista

```
version: '2'
services:
  web:
    build:                                          # equivalente ao docker-build
      context: ./dir
      dockerfile: Dockerfile-alternate              # equivalente ao -f do docker build
      args:
        versao:1                                    # equivalente ao build-args
      ports:
        - "5000:5000"                               # equivalente ao parâmerto -p
  redis:
      image: redis                                  # busca imagem no hub.docker.com, por padrão
```

Versões do docker-compose: https://docs.docker.com/compose/compose-file/#versioning

* build : Usado para constuir imagens
* up : Inciar todos serviços que estão no arquivo docker-compose.yml
* stop : Parar todos serviços que estão no docker-compose.yml
* ps : Lista todos serviços iniciador a partir do docker-compose.yml


# Revisar
```console
docker ps
docker ps -a
docker container -a
docker start -a ubuntu
docker rm
docker container prune

docker images
docker rmi hello-world

docker run -d -P --name meu-site dockersamples/static-site
sudo docker run -d -p 12345:80 dockersamples/static-site

variável de ambiente
docker run -d -P -e AUTHOR="Yan" dockersamples/static-site
sudo docker port f405f

docker ps -q
sudo docker stop $(docker ps -q)

Volumes
sudo docker run -it -v "/home/yan/docker:/var/www" ubuntu

sudo docker run -v "/home/yan/docker:/var/www" -p 8080:3000 -w "/var/www/volume-exemplo" node npm start

sudo docker run -d -v "$(pwd):/var/www" -p 8080:3000 -w "/var/www/volume-exemplo" node npm start

sudo docker inspect 92834

Dockerfile 

também funciona ubuntu.dockerfile   mongo.dockerfile

FROM node:latest
MAINTAINER Yan Fonseca
ENV NODE_ENV=production
ENV PORT=3000
COPY . /var/www
WORKDIR /var/www
RUN npm install
ENTRYPOINT npm start
EXPOSE $PORT

docker network ls
docker network inspect minharede

 sudo docker build -f Dockerfile -t yanf/node . 
 sudo docker run -d -p 1234:3000 yanf/node
 
 hostname -i
 apt-get update && apt-get install -y iputils-ping
 ping 172.17.0.3
 
 criar rede, 
 
 para fazer referencia ao ip,
 na rede bridge só com o número do ip
 se criar a própria rede é possível fazer referencia pelo nome 
 
 criar própria rede
 docker network create --driver bridge minharede
sudo docker run -it --name containerubuntu --network minharede ubuntu

docker rm -f 324

 
```
