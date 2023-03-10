#### Acessar o bash do container em modo iterativo
```bash
docker exec -it <container> /bin/bash
```
#### Acessar como root
```bash
docker exec -u 0 <container> <command>
```

#### Limpando todas as imagens, contêineres, volumes e redes não utilizados ou pendentes
```bash
# Limpar imagens, contêineres, volumes e redes que estejam pendentes 
docker system prune

# Limpar imagens não utilizadas, contêineres interrompidos, volumes e redes 
docker system prune -a
```


<br><br>

## Lista de comandos do Docker e sua utilidade

Comando        | Finalidade      
-------------- | -------------------------------
docker attach  |Acessar dentro do container e trabalhar a partir dele. 
docker build   |A partir de instruções de um arquivo Dockerfile eu possa criar uma imagem. 
docker commit  |Cria uma imagem a partir de um container.
docker cp      |Copia arquivos ou diretórios do container para o host.
docker create  |Cria um novo container.
docker diff    |Exibe as alterações feitas no filesystem do container.
docker events  |Exibe os eventos do container em tempo real.
docker exec    |Executa uma instrução dentro do container que está rodando sem precisar atachar nele.
docker export  |Exporta um container para um arquivo .tar.
docker history |Exibe o histórico de comandos que foram executados dentro do container.
docker images  |Lista as imagens disponíveis no host.
docker import  |Importa uma imagem .tar para o host.
docker info    |Exibe as informações sobre o host.
docker inspect |Exibe r o json com todas as configurações do container.
docker kill    |Da Poweroff no container.
docker load    |Carrega a imagem de um arquivo .tar.
docker login   |Registra ou faz o login em um servidor de registry.
docker logout  |Faz o logout de um servidor de registry.
docker logs    |Exibe os logs de um container.
docker port    |Abre uma porta do host e do container.
docker network |Gerenciamento das redes do Docker.
docker node    |Gerenciamento dos nodes do Docker Swarm.
docker pause   |Pausa o container.
docker port    |Lista as portas mapeadas de um container.
docker ps      | Lista todos os contêineres.
docker pull    |Faz o pull de uma imagem a partir de um servidor de registry.
docker push    |Faz o push de uma imagem a partir de um servidor de registry.
docker rename  |Renomeia um container existente.
docker restart |Restarta um container que está rodando ou parado.
docker rm      |Remove um ou mais containeres.
docker rmi     |Remove uma ou mais imagens.
docker run     |Executa um comando em um novo container.
docker save    |Salva a imagem em um arquivo .tar.
docker search  |Procura por uma imagem no Docker Hub.
docker service |Gernciamento dos serviços do Docker.
docker start   |Inicia um container que esteja parado.
docker stats   |Exibe informações de uso de CPU, memória e rede.
docker stop    |Para um container que esteja rodando.
docker swarm   |Clusterização das aplicações em uma orquestração de várias containers, aplicações junto.
docker tag     |Coloca tag em uma imagem para o repositorio.
docker top     |Exibe os processos rodando em um container.
docker unpause |Inicia um container que está em pause.
docker update  |Atualiza a configuração de um ou mais containers.
docker version |Exibe as versões de API, Client e Server do host.
docker volume  |Gerenciamento dos volumes no Docker.
docker wait    |Aguarda o retorno da execução de um container para iniciar esse container.

Obs.: É possível ver todos os comandos que o Docker possui, tendo o docker instalado, basta digitar no terminal docker --help


<br><br>


#### enter a specific docker conteiner
```bash
docker exec -it -u <use> <name_container> bash
docker exec -it <name_container> bash //without user
```

#### up all docker containers
```bash
docker-compose up -d
```

#### stop all docker containers
```bash
docker-compose stop
```

#### remove a specific docker container
```bash
docker rm <name_container>
```

#### remove all containers
```bash
docker rm -f $(docker ps -a -q)
docker rm -f $(docker ps -qa)
```

#### list all docker containers with id, image (location), command, created, status, ports, names
```bash
docker ps -a
```

#### remove orphans images
```bash
docker rmi $(docker images | grep "^<none>" | awk "{print $3}")
```

#### remove just of exited containers
```bash
docker rm $(docker ps -qa -f status=exited)
```

#### remover todas as imagens
```bash
docker image rm -f $(docker image ls -aq)
docker rmi -f $(docker image ls -aq))
```

#### remover todos os Volumes
```bash
docker volume rm $(docker volume ls -q)
```

#### inspect an image
```bash
docker history my/image | awk 'NR>1 {print $1}' | xargs docker inspect --format '{{ ((index .ContainerConfig.Cmd ) 0) }}'

docker stop $(docker ps -q); docker rm $(docker ps -a -q); docker volume rm $(docker volume ls -q); docker rmi $(docker images -q); docker network rm $(docker network ls -q);
docker command to clear all
```

#### show docker disk usage
```bash
docker system df
```

#### show docker disk usage - verbose mode
```bash
docker system df -v
```

#### stop and remove containers, networks..
```bash
docker-compose down 
```bash

#### stop and remove containers, networks.. - verbose mode
```bash
docker-compose down -v
```

#### down and remove volumes
```bash
docker-compose down --volumes 
```

#### down and remove images
```bash
docker-compose down --rmi <all|local> 
```
