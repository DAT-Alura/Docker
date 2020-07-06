# Perguntas

## Aula 1

Vimos que utilizar um servidor físico separado para cada serviço do nosso sistema gera vários problemas, entre eles o custo de luz e rede, e o seu alto tempo de ociosidade.

A solução para esses problemas foi a virtualização dos recursos físicos, reduzindo assim os custos de luz e rede, já que não teremos mais vários servidores físicos, e não teremos mais ociosidade do hardware.

Mas as máquinas virtuais também possuem problemas, que estão listados abaixo, exceto um. Qual?

- Como as máquinas virtuais possuem sistemas operacionais, os mesmos possuem um custo de hardware para manter suas funcionalidades.
- Como as máquinas virtuais possuem sistemas operacionais, os mesmos possuem configurações iniciais a serem feitas, e devem ser atualizados com frequência.
- Manter vários sistemas operacionais requer muito tempo de trabalho, chegando a equivaler ao tempo requerido para manter as aplicações
- __A dificuldade em fazer um backup de dos dados.__

>Esse não é um problema das máquinas virtuais! O backup dos dados de uma máquina virtual pode ser feito com certa facilidade, seja por softwares externos ou através das próprias VMs.

Eduardo está encarregado de convencer seu chefe a utilizar containers na infraestrutura de sua empresa. Para isso criou alguns slides para apresentar suas ideias. Um slide específico está intitulado Benefícios dos Containers, com os tópicos abaixo. Contudo, um deles não é um benefício do uso de containers. Ajude Eduardo apontando qual alternativa está errada.

- Melhor controle do uso dos recursos do sistema operacional.
- Agilidade na hora de criar e remover aplicações
- __O fato de ter um sistema operacional instalado em cada container permite o isolamento de conflitos de rede e versões.__
- Maior facilidade na hora de trabalhar com diferentes versões de bibliotecas e linguagens.

> Isso aí. Eduardo precisa remover esse tópico, porque além de não ser um benefício, está errado afirmar que cada container possui um SO instalado.

Selecione apenas as alternativas que são tecnologias Docker.

- dotCloud
- Docker Inc.
- __Docker Engine__
- __Docker Hub__
- __Docker Swarm__

> Docker Engine: Isso aí! Essa é a tecnologia mais famosa e responsável por fazer o meio de campo entre os containers e o SO.  
> Docker Hub: Isso aí! O Docker Hub provê um repositório com muitas aplicações para você usar em sua infraestrutura.  
> Docker Swarm: Isso aí! Essa tecnologia permite o uso de múltiplos docker hosts.

## Aula 2

Temos os seguintes comandos do Docker e suas respectivas funcionalidades:

1) O comando docker ps nos permite ver todos os container já criados

2) O comando docker container prune permite remover todos os containers inativos de uma só vez.

3) O comando docker rm ID_DO_CONTAINER remove um container

Quais funcionalidades, e seus respectivos comandos, estão corretas?

- Funcionalidade 1
- __Funcionalidade 2__
- __Funcionalidade 3__

> Funcionalidade 2: Alternativa correta! O comando docker container prune realmente apaga todos os containers inativos, mas dá um aviso antes.  
> Funcionalidade 3: Alternativa correta! O comando docker rm ID_DO_CONTAINER permite remover um container especifico.

Temos as seguintes afirmações sobre o Layered File System:

A) Toda imagem que baixamos é composta de uma ou mais camadas.

B) Essas camadas podem ser reaproveitadas em outras imagens, acelerando assim o tempo de download.

C) As camadas de uma imagem são de escrita e leitura

Qual dessas afirmações é falsa?

- A é falsa
- B é falsa
- __C é falsa__

> Realmente é falsa pois as camadas na imagem são de leitura apenas.

Luis resolveu acessar sua aplicação, chamada de MinhaAplicacao e que está dentro do container, utilizando a porta 8080 a partir de sua máquina. Porém, como é novo no ramo do Docker, ele está em dúvida sobre qual comando deve utilizar para saber quais são as portas mapeadas. Marque a opção que realiza o desejo de Luis:

- Luis deve usar o comando 'docker run MinhaAplicacao'.
- __Luis deve usar o comando 'docker port ID_DO_CONTAINER'  para que possa saber qual porta de sua máquina faz referência à porta 8080 de seu container.__
- Luis deve usar o comando 'docker rmi MinhaAplicacao'.

## Aula 3

Por que usamos volumes?

- Containers não guardam nenhum dado (são read-only) e por isso precisamos de volumes.
- __Muitas vezes removemos os containers após o uso. Volumes são usados para os dados que não devem ser removidos.__
- O uso dos volumes simplifica a execução pois não precisamos mais de imagens.

> Correto, é muito comum usar o container e apagá-lo após seu uso. Dessa forma também são removidos os dados desse container e aí entram os volumes que permitem salvar dados fora do container.

Um volume fica salvo:

- Na Imagem
- __No Docker Host__
- No Container

> Correto, o volume fica no Docker Host. Ou seja, fica salvo no computador onde a Docker Engine está rodando.

Qual dos comandos abaixo configura o volume do diretório /var/www do container para C:\logs do Host?

- docker run -v "/var/www" ubuntu
- docker run -v "C:\logs" ubuntu
- __docker run -v "C:\logs:/var/www" ubuntu__
- docker run "C:\logs:/var/www" ubuntu

> Correto, usando a flag -v seguindo pelo CAMINHO_HOST:CAMINHO_CONTAINER.

Flavio é um programador com muita experiência no mundo Javascript, porém agora resolveu se aventurar no mundo do Docker. Ao pensar em como iria organizar os caminhos dos volumes em sua máquina e container, ele executou o comando docker inspect. Abaixo temos um pedaço da saída do comando docker inspect ID_DO_CONTAINER no terminal de Flavio, sobre a saída abaixo é verdade que:

```json
"Mounts": [
    {
        "Type": "volume",
        "Name": "5e1cbfd48d07284680552e56087c9d5196659600ccd6874bfa3831b51ddd0576",
        "Source": "/home/Flavio/Desktop/volumes/caminho/_data",
        "Destination": "/var/opt",
        "Driver": "local",
        "Mode": "",
        "RW": true,
        "Propagation": ""
    }
]
```

- "/var/opt" e "/home/Flavio/Desktop/volumes/caminho/_data" pertencem ao container.
- "/var/opt" e "/home/Flavio/Desktop/volumes/caminho/_data" pertencem à máquina.
- "/home/Flavio/Desktop/volumes/caminho/_data"  pertence ao container e será armazenado no caminho "/var/opt" em nossa máquina.
- __"/var/opt" pertence ao container e será escrito no caminho "/home/Flavio/Desktop/volumes/caminho/\_data" em nossa máquina.__

> Correto! "/var/opt" pertence ao container enquanto "/home/Flavio/Desktop/volumes/caminho/_data" pertence à máquina e irá armazenar "/var/opt".

## Aula 4

1 - No primeiro dia de trabalho de Fernando, ele encontrou um Dockerfile chamado ns.dockerfile:

```Dockerfile
FROM node:latest
MAINTAINER Ubuntu
COPY . /var/www
WORKDIR /var/www
RUN npm install
ENTRYPOINT npm start
EXPOSE 3000
```

Marque as alternativas verdadeiras sobre o Dockerfile encontrado por Fernando:

- __A imagem se baseia na imagem node. Inclusive o container se baseará sempre na última versão da imagem.__
- __Todo o conteúdo que será copiado para a imagem ficará dentro da pasta '/var/www'.__
- Em MAINTAINER indicamos a versão do sistema operacional que utilizaremos.
- EXPOSE indica quanto tempo o container ficara no ar.

2 - Guilherme Nicolau recebeu as seguintes instruções para criação de um docker container:

- Deve instalar o mysql da última imagem disponível
- Os dados iniciais devem ser copiados para a pasta /etc/sinc
- O diretório de trabalho deve ser /etc/sinc/plen
- A porta de comunicação deve ser 1711
- O comando de entrada chmod 755 /etc/sinc

Marque a opção que possui a configuração de um Dockerfile condizente com a especificação passada para Guilherme:

A)

```Dockerfile
FROM mysql:latest
MAINTAINER Guilherme Nicolau
COPY . /etc/sinc/plen
WORKDIR /etc/sinc
EXPOSE 1711
```

__B__)

```Dockerfile
FROM mysql:latest
MAINTAINER Guilherme Nicolau
COPY . /etc/sinc
WORKDIR /etc/sinc/plen
ENTRYPOINT chmod 755 /etc/sinc
EXPOSE 1711
```

C)

```Dockerfile
FROM mysql:latest
MAINTAINER Guilherme Nicolau
COPY /etc/sinc/plen
WORKDIR . /etc/sinc
ENTRYPOINT chmod 755 /etc/sinc
EXPOSE 1711
```

D)

```Dockerfile
FROM mysql:latest
MAINTAINER Guilherme Nicolau
WORKDIR /etc/sinc/plen
ENTRYPOINT chmod 755 /etc/sinc
EXPOSE 1711
```
