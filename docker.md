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
| -l        | Lista últimos contaêineres|
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

    O -t é o parâmetro para informar o nome da imagem:

    docker image build -t nome_da_imagem:versao_da_imagem
    
### Armazenamento no Docker

* Mapeamento de pasta específica do host que pode ser compartilhada com contêiner. 
Lembrando a regra host:container ainda é válida aqui.

    docker container run -v /var/lib/container1:/var ubuntu

* Volume em um contêiner que vai ser consumido por outros contêiners(contêiner especial).

    docker create -v /dbdata --name dbdata postgres /bin/true

    Para consumir o volume do contatêiner acima:

        docker container run -d --volumes-from dbdata --name db2 postgres

    Dessa forma, o contêiner db2 terá pasta dbdata do contêiner dbdata, 
    o que facilita na portabilidade dos contêineres já que existe independência 
    em relação ao host.

* Na versão 1.9 foi criada a possibilidade de criar volumes 
isolados de contêineres e que podem ser consumidos por quaisquer contêineres.

    docker volume create --name dbdata

    * É necessário associar uma pasta de dentro do contêiner com o volume isolado. 

    docker container run -d -v dbdata:/var/lib/data postgres

### Rede no Docker

    docker network ls

* Bridge - Rede padrão para os contêineres. Cria uma interface que faz a ponte entre 
    docker0 do docker host. Recebe o endereço de ip automaticamente.

    Se o docker host tiver acesso a a internet, os contêineres também terão.

* none - Serve para isolar o contêiner para comunicações externas e não recebe 
interface para comunicação externa e somente a interface com localhost. É uma rede usada para 
contêineres que manipulam arquivos e não precisam enviá-los para outro local. Por exemplo, 
o contêiner de back up que através do volume de contêiner de banco de dados faz o dump.

    
* host

* Redes que podem ser criadas com o: 

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
