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


