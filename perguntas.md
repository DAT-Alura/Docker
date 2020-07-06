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
