# 1. Docker

- [1. Docker](#1-docker)
  - [1.1. Overview](#11-overview)
    - [1.1.1. O que é Docker?](#111-o-que-é-docker)
    - [1.1.2. Recursos oferecidos](#112-recursos-oferecidos)
    - [1.1.3. Conceitos](#113-conceitos)
      - [1.1.3.1. O que é um contêiner?](#1131-o-que-é-um-contêiner)
      - [1.1.3.2. O que é uma imagem de contêiner?](#1132-o-que-é-uma-imagem-de-contêiner)
      - [1.1.3.3. Definições](#1133-definições)
  - [1.2. Hands-on](#12-hands-on)
    - [1.2.1. WSL - Windows Subsystem for Linux](#121-wsl---windows-subsystem-for-linux)
      - [1.2.1.1. Instalação](#1211-instalação)
      - [1.2.1.2. Dicas](#1212-dicas)
        - [1.2.1.2.1. *#01 - Terminal do Windows*](#12121-01---terminal-do-windows)
        - [1.2.1.2.2. *#02 - Acessar Linux Home - pelo Windows:*](#12122-02---acessar-linux-home---pelo-windows)
        - [1.2.1.2.3. *#03 - Integração Linux e Windows: Abrir no Windows Explorer*](#12123-03---integração-linux-e-windows-abrir-no-windows-explorer)
        - [1.2.1.2.4. *#04 - VS Code - plugin - "Remote Development"*](#12124-04---vs-code---plugin---remote-development)
        - [1.2.1.2.5. *#05 - Power Shell*](#12125-05---power-shell)
        - [1.2.1.2.6. *#06 - Configurar recursos da sua máquina para o WSL*](#12126-06---configurar-recursos-da-sua-máquina-para-o-wsl)
        - [1.2.1.2.7. *#07 - Backup do WSL 2*](#12127-07---backup-do-wsl-2)
    - [1.2.2. Instalar Docker no WSL 2](#122-instalar-docker-no-wsl-2)
    - [1.2.3. Docker CMD](#123-docker-cmd)
      - [1.2.3.1. Iniciar e consultar contêiners](#1231-iniciar-e-consultar-contêiners)
      - [1.2.3.2. Remover contêiners](#1232-remover-contêiners)
      - [1.2.3.3. Bash em contêiners](#1233-bash-em-contêiners)
      - [1.2.3.4. Volumes](#1234-volumes)
      - [1.2.3.5. Imagens](#1235-imagens)
      - [1.2.3.6. Remover todos os containers e imagens](#1236-remover-todos-os-containers-e-imagens)
      - [1.2.3.7. Network](#1237-network)
    - [1.2.4. Dockerfile](#124-dockerfile)
      - [1.2.4.1. Definir a imagem - (reserved words)](#1241-definir-a-imagem---reserved-words)
    - [1.2.6. Docker Compose](#126-docker-compose)
    - [1.2.5. Frameworks e ambiente para desenvolvimento](#125-frameworks-e-ambiente-para-desenvolvimento)
      - [1.2.5.1. Node](#1251-node)
      - [1.2.5.2. Java developer](#1252-java-developer)
      - [1.2.5.3. Java developer - c/ Dockerfile](#1253-java-developer---c-dockerfile)
      - [1.2.5.4. Java release - c/ Dockerfile](#1254-java-release---c-dockerfile)
    - [Exclusão de imagens e contêiners em lote](#exclusão-de-imagens-e-contêiners-em-lote)

---

## 1.1. Overview

### 1.1.1. O que é Docker?

O Docker é uma plataforma de software open source que possibilita o empacotamento de uma aplicação dentro de um container.[^1] [^2]
  
Com o Docker é possível criar, implantar e executar aplicativos em contêiners. Esses contêiners fornecem um ambiente isolado para os aplicativos e suas dependências, tornando-os portáveis e fáceis de implantar em diferentes plataformas e ambientes.[^3]

[^1]: Docker overview<br>
  Disponível em: https://docs.docker.com/get-started/<br>
  Consultado em: 01/04/2023

[^2]: Curso FullCycle - Docker<br>
  Consultado em: 18/09/2022<br>
  Disponível em: https://plataforma.fullcycle.com.br

[^3]: OpenIA -> "Apresente um resumo breve dos recursos oferecidos pelo Docker"<br>
  Disponível em: https://chat.openai.com/chat<br>
  Consultado em: 01/04/2023

---

### 1.1.2. Recursos oferecidos

1. Isolamento de aplicativos em contêiners: cada contêiner tem seu próprio ambiente isolado para executar o aplicativo e suas dependências, o que ajuda a garantir a compatibilidade e a segurança.

2. Portabilidade de aplicativos: os contêiners são portáteis e podem ser executados em qualquer sistema operacional ou infraestrutura de nuvem compatével com Docker.

3. Gerenciamento de recursos: o Docker ajuda a gerenciar os recursos do sistema, incluindo CPU, memória e armazenamento, para garantir que os aplicativos executem de forma eficiente.

4. Escalonamento horizontal: o Docker permite dimensionar facilmente aplicativos com vários contêiners em diferentes hosts para lidar com cargas de trabalho crescentes.

5. Implantação de aplicativos: os contêiners podem ser facilmente implantados em diferentes ambientes, incluindo nuvem pública, nuvem privada, data center local ou laptop.

6. Integração contínua e implantação contínua (CI/CD): o Docker pode ser integrado a ferramentas de CI/CD para automatizar o processo de construção, teste e implantação de aplicativos e contêiners.

Esses recursos tornam o Docker uma das plataformas de contêiners mais populares e amplamente usadas no mundo do desenvolvimento de software e da computação em nuvem [^3].

<br>

---

### 1.1.3. Conceitos

#### 1.1.3.1. O que é um contêiner?

Simplificando, um contêiner é um processo empacotado em sua máquina que é isolado de todos os outros processos na máquina host. Este isolamento aproveita o namespaces do kernel e cgroups, funcionalidades que estão no Linux há muito tempo. O Docker trabalhou para tornar esses recursos acessíveis e fáceis de usar [^1].

Para resumir um contêiner:
- É uma instância executável de uma imagem. Você pode criar, iniciar, parar, mover ou deletar um contêiner usando o Docker API ou CLI.
- Pode ser executado em máquinas locais, máquinas virtuais ou implantado na Cloud
- É portável (pode ser executado em qualquer OS)
- É isolado de outros contêiners e roda seu próprio software, binários e configurações

---

> :memo: **Nota sobre sistema operacional (OS):** 

> Namespace (Espaço de nomes): Um espaço de nomes é um delimitador abstrato que fornece um contexto para os itens que ele armazena, o que permite uma desambiguação para itens que possuem o mesmo nome mas que residem em espaços de nomes diferentes [^4].

> CGroups: Fornece recursos para controlar CPU, Memória

> File System: Overlay File System (OFS) - Camadas individualizadas

[^4]: Namespace<br>
  Disponível em: https://pt.wikipedia.org/wiki/Espa%C3%A7o_de_nomes<br>
  Consultado em: 01/04/2023

---

#### 1.1.3.2. O que é uma imagem de contêiner?

Quando um contêiner é executado, ele utiliza um sistema de arquivos (filesystem) isolado. Este sistema de arquivos é provido pela imagem do contêiner. Uma vez que a imagem possui o sistema de arquivos do contêiner, ela pode conter todas as coisas necessárias para executar um aplicativo - todas as dependências, configurações, scripts, binários, etc. A imagem também contém outras configurações para o contêiner, como variáveis de ambiente, um comando de inicialização padrão, e outros metadados[^1].

#### 1.1.3.3. Definições

- Dockerfile: um arquivo declarativo de como "Construir a imagem".

- Image registry: onde ficam as imagens.

- Docker client: Utilitário para criar contêiner, rodar contêiner, gerir volumes e administrar network.

- Docker host: É o sistema host do contêiner, onde fica o daemon API, que fornece os recursos para manter Volume dos sistema operacional, Network de comunicação entre conteiners e Cache do Registry.

- Docker Engine: É o Docker Nativo, e vem diretamente instalado no WSL2.

---

## 1.2. Hands-on

### 1.2.1. WSL - Windows Subsystem for Linux

#### 1.2.1.1. Instalação

https://github.com/codeedu/wsl2-docker-quickstart

#### 1.2.1.2. Dicas

##### 1.2.1.2.1. *#01 - Terminal do Windows*

https://learn.microsoft.com/pt-br/windows/terminal/

##### 1.2.1.2.2. *#02 - Acessar Linux Home - pelo Windows:*

`\\wsl$\Ubuntu\home\`

##### 1.2.1.2.3. *#03 - Integração Linux e Windows: Abrir no Windows Explorer*

`$ explorer.exe .`

##### 1.2.1.2.4. *#04 - VS Code - plugin - "Remote Development"*

https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack

##### 1.2.1.2.5. *#05 - Power Shell*

`PS> wsl --help`

```shell
PS> wsl -l -v
  NAME            STATE           VERSION
* Ubuntu          Running         2
  Ubuntu-20.04    Stopped         2
```

  Pamâmetros:<br>
  -l = Listas<br>
  -v = Versions	
	
`PS> wsl --shutdown			-> Parar todas as versões WSL	`

##### 1.2.1.2.6. *#06 - Configurar recursos da sua máquina para o WSL*

  C:\Users\domingues.marcos\.wslconfig

##### 1.2.1.2.7. *#07 - Backup do WSL 2*

```
  Arquivo de Máquina Virtual:
		Nome: ext4.vhdx
		Local: C:\Users\domingues.marcos\AppData\Local\Packages\CanonicalGroupLimited.Ubuntu_79rhkp1fndgsc\LocalState
	
	Recuperar:
		- Instalar um novo Ubuntu (pelo Microsoft Store)
		-	Criar mesmo usuário e senha ( do backup )
		- Copiar o arquivo 'ext4.vhdx'
```

---

### 1.2.2. Instalar Docker no WSL 2

```sh
# Pré-requisitos

$ sudo apt update && sudo apt upgrade
$ sudo apt remove docker docker-engine docker.io containerd runc
$ sudo apt-get install \
    apt-transport-https \
    ca-certificates \
    curl \
    gnupg \
    lsb-release
```

```sh
# Adicione o repositório do Docker na lista de sources do Ubuntu:

$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
$ echo \
  "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```sh
# Instale o Docker Engine

	$ sudo apt-get update
	$ sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

```sh
# Dê permissão para rodar o Docker com seu usuário corrente:

$ sudo usermod -aG docker $USER
```

```sh
# Iniciando o serviço do Docker:

$ sudo service docker start
```

```sh
# Verifique se está OK

$ docker ps
```

```sh
# Se não estiver Ok, rode o comando abaixo e escolha a opção 1 legacy:

$	sudo update-alternatives --config iptables
```

```sh
# Verifique NOVAMENTE se está OK

$ sudo service docker start
$ docker ps
```

```sh
# Errata - Instalação do Docker no WSL/Windows
# Atualmente o Docker Engine (Docker Nativo) para o Windows trouxe muitos recursos e vantagens em comparação ao Docker Desktop, fazendo assim que tenhamos performance e diminuindo o consumo de memoria RAM, por isso sugerimos a vocês utilizarem o Docker Engine.

# Abaixo temos um vídeo gravado que ensina a realizar a instação do Docker Engine no WSL2.
# https://www.youtube.com/watch?v=wpdcGgRY5kk

# Repositório com algumas informações sobre a instalação e pontos importantes sobre o Docker Engine.
# https://github.com/codeedu/wsl2-docker-quickstart#docker-engine-docker-nativo-diretamente-instalado-no-wsl2
```

---

### 1.2.3. Docker CMD

#### 1.2.3.1. Iniciar e consultar contêiners

```sh
# Iniciar o serviço docker no WSL

$ sudo service docker start
```

```sh
# Listar containers

$ docker ps           # -> Listar containers rodando
$ docker ps -a        # -> Listar TODOS os containers
```

```sh
# Rodar um container

$ docker run hello-world            # -> Rodar container
$ docker run -it ubuntu bash        # -> Rodar 'ubuntu' e abrir o bash (i=iterativo, t=tty)
$ docker run -it --rm ubuntu bash   # -> Rodar 'ubuntu', abrir o bash & remover a imagem ao sair
$ docker run -d -p 8080:80 nginx    # -> Rodar 'ubuntu', abrir o bash, vincular a porta 8080:80 & remover a imagem ao sair sem prender o terminal

$ docker run -d --name nginx -p 8080:80 nginx

$ docker run -e JAVA_HOME "/usr/jdk/"
```

```sh
# Parar ou iniciar um container

$ docker stop f417e306e471
$ docker start f417e306e471
```

#### 1.2.3.2. Remover contêiners

```sh
# Remover o container

$ docker rm musing_hopper     # -> Remover usando o nome do container
$ docker rm 0956e096b381      # -> Remover usando o ID do container

# Remover e forçar a remoção (se estiver rodando)

$ docker rm 0956e096b381 -f
```

#### 1.2.3.3. Bash em contêiners

```sh
# Executar/entrar um comando 'bash' dentro do container

$ docker exec nginx ls        # -> Rodar o comando 'ls' dentro do container
$ docker exec -it nginx bass  # -> Entrar no 'bash'
```

```sh
# Para entrar no 'bash'

$ docker attach ubuntu1
```

#### 1.2.3.4. Volumes

```sh
# Montar pasta - volumes (antigo)

$ docker run -d --name nginx -p 8080:80 -v ~/projects/fullcycle/docker/html/:/usr/share/nginx/html nginx
```

```sh
# Montar pasta - volumes (bind mount)

		--mount
			type=
			source=
			target=
	
	$ docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/html,target=/usr/share/nginx/html nginx
```

```sh
# Volumes

$ docker volume
$ docker volume ls                  # -> Listar os volumes
$ docker volume create meuvolume    # -> Criar novo
$ docker volume inspect meuvolume   # -> Exibir detalhes
```

```sh
# Montar utilizando volumes

$ docker run --name nginx -d --mount type=volume,source=meuvolume,target=/app nginx
$ docker exec -it nginx bash
$ cd app
$ touch oi

$ docker run --name nginx2 -d --mount type=volume,source=meuvolume,target=/app nginx
$ docker exec -it nginx2 bash
$ cd app
$ ls

$ docker run --name nginx3 -d -v meuvolume:/app nginx
$ docker exec -it nginx3 bash
$ cd app
$ ls
```

#### 1.2.3.5. Imagens

```sh
# Imagens
# -> https://hub.docker.com/

$ docker pull ubuntu        # -> Baixar do registry do Docker-Hub
$ docker images             # -> Exibir todas
$ docker rmi nginx:latest   # -> Remover
```

#### 1.2.3.6. Remover todos os containers e imagens

```sh
# Remover todos os containers e imagens

$ docker rm $(docker ps -a -q) -f
$ docker rmi $(docker images -q)

$ docker network prune

$ docker ps -a
$ docker images -a
```

#### 1.2.3.7. Network

```sh
# Network - tipos

#		bridge      - (Ponte), Rede 'default' criada qdo não informa nada
#		host        - Mescla a rede do 'container' docker com o 'host' do docker
#		overlay     - (Docker Swarm) Para q um container consiga falar com outro em outra máquina
#		maclan      - 
#		none        - Não vai ter rede no container
```

```sh
# Network	- (bridge)

$ docker network                            -> Network help
$ docker network ls                         -> Listar redes
$ docker network inspect bridge             -> Ver detalhes
$ docker network prune                      -> Excluir não utilizadas
$ docker network connect minharede ubuntu3  -> Conectar um container em uma 'network'

```

```sh
# NETWORK - 'host' acessar 'container'
	
# -> Ao vincular o container com 'host', a rede local estará acessível/integrada
# -> Desta forma não precisará mapear portas
# -> Portanto ao subir o nginx será possível ver o 'Welcome page'

$ docker run -d --rm --name nginx --network host nginx
$ curl http://localhost
```


---

### 1.2.4. Dockerfile

Docker file é a 'Receita de bolo' para criar imagens

#### 1.2.4.1. Definir a imagem - (reserved words)

| word       | Description                                       |
| ---------- | ------------------------------------------------- |
| FROM       | Imagem base                                       |
| USER       | Usuário                                           |
| ENV        | Variável de ambiente                              |
| WORKDIR    | Diretório 'default' de trabalho                   |
| RUN        | Executar comandos bash                            |
| COPY       | Copiar arquivos                                   |
| EXPOSE     | Expor uma a porta                                 |
| ENTRYPOINT | Comando (fixo) executado ao rodar o container     |
| CMD        | Comando (variável) executado ao rodar o container |

```sh
# Dockerfile > image > exemplo #01

FROM nginx:latest

RUN apt-get update && \
    apt-get install vim -y

ENV NGINX_VERSION 1.23.1
EXPOSE 80
```

```sh
# Criar imagem - usando 'Dockerfile'

$ docker build -t mdominguesdev/nginx-com-vim:latest .
	
		# -> O ponto '.' significa em que pasta está o 'Dockerfile'
```

```sh
# Dockerfile > image > exemplo #02

FROM ubuntu:latest
ENTRYPOINT [ "echo", "Hello " ]
CMD [ "World" ]
```

```sh
# Resultado exemplo #02 - executar com parâmetros

$ docker build -t mdominguesdev/hello .

$ docker run --rm  mdominguesdev/hello
  # -> Hello World
  
$ docker run --rm  mdominguesdev/hello Marcos
  # -> Hello Marcos
  
$ docker run --rm  mdominguesdev/hello X
  # -> Hello X
  
  # -> O ENTRYPOINT "echo Hello " continua fixo
  # -> O CMD mudou com a entrada de parâmetros
```

```sh
# Enviar imagem p/ docker hub

$ docker build -t -p 8080:80 mdominguesdev/nginx-fullcycle .
$ docker run -d --rm -p 8080:80 mdominguesdev/nginx-fullcycle	
$ docker login
$ docker push mdominguesdev/nginx-fullcycle
```

---

### 1.2.6. Docker Compose

```sh
# docker-compose.yaml

version: '3'

services:
  laravel:
    build:
      context: ./laravel
      dockerfile: Dockerfile.prod
    image: mdominguesdev/laravel:prod
    container_name: laravel
    networks:
    - laranet
  nginx:
    build:
      context: ./nginx
      dockerfile: Dockerfile.prod
    image: mdominguesdev/nginx:prod
    container_name: nginx
    networks:
    - laranet
    ports:
    - "8080:80"

networks:
  laranet:
    driver: bridge
```

```sh
# Docker compose commands

$ docker compose up -d
$ docker compose up -d --build
$ docker compose ps

$ docker compose down
$ docker compose stop db
```

---

### 1.2.5. Frameworks e ambiente para desenvolvimento

#### 1.2.5.1. Node
```sh
# Node

$ docker run --rm -it -v $(pwd)/:/usr/src/app -p 3000:3000 node:15 bash
  # -> http://localhost:3000/
```

#### 1.2.5.2. Java developer
```sh
# Java developer - usando o volume

		$ docker run -it --rm --name openjdk19 -v $(pwd)/:/usr/src/app  openjdk:19 bash
```

#### 1.2.5.3. Java developer - c/ Dockerfile
```sh
# Dockerfile

FROM openjdk:19
WORKDIR /usr/src/app
RUN apt-get update
EXPOSE 8080
CMD ["/bin/bash"]
```

```sh
# Rodar

$ docker run -it --rm --name openjdk19 -v $(pwd)/:/usr/src/app  mdominguesdev/openjdk19 bash
```

#### 1.2.5.4. Java release - c/ Dockerfile
```sh
# Dockerfile

FROM openjdk:19
WORKDIR /usr/src/app
COPY . .
RUN apt-get update && apt-get install ...
RUN mvn install
EXPOSE 8080
CMD ["java", "/usr/src/app/myapplication"]
```

---

### Exclusão de imagens e contêiners em lote

> :warning:  **ATENÇÃO:** Os comandos abaixo irão remover todas as imagens e contêiners.

```sh
# Remover todos os containers e imagens

$ docker rm $(docker ps -a -q) -f
$ docker rmi $(docker images -q)

$ docker network prune

$ docker ps -a
$ docker images -a
```