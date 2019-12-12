---
layout:	"post"
categories:	"blog"
title:	"LAMP no Debian, Ubuntu e derivados (2019)"
date:	2019-03-10
thumbnail:	/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg
author:	
---

* * *

**Aten çao:** O pacote phpmyadmin nao esta presente nos repositorios do Debian
Buster e do Ubuntu Eoan, vou escrever outro para essas versoes.

 **phpMyAdmin no Debian Buster e Ubuntu Eoan** :
<https://medium.com/@leandroembu/phpmyadmin-no-debian-buster-ba7325ed3bd2>

![](/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg)

LAMP -- Imagem "chupinhada" de <https://www.unixmen.com/how-to-install-lamp-
stack-ubuntu-17-04/>

Ola, pessoal. Beleza?

Muita gente tem dificuldade para subir um ambiente LAMP em distribuiçoes
Linux, especialmente na hora de configurar os acessos ao servidor de banco de
dados com o famoso phpMyAdmin. Vou tentar mostrar em poucos passos como voce
pode fazer para subir a pilha Apache + MariaDB + PHP no Elementary OS, mas os
passos sao os mesmos no Debian, Ubuntu e seus derivados.

Video (veja na pratica):

#### Instalando o Apache

    
    
    sudo apt install apache2

Apos a instalaçao, abra o navegador em <http://localhost>. Voce devera ver
algo como na imagem abaixo:

![](/img/1*kmpSFoFesuRHlsfv6YoNVA.png)

Apache2 Homepage

* * *

#### Instalando o MariaDB

    
    
    sudo apt install mariadb-server

Apos a instalaçao, e necessario fazer a configuraçao inicial do MariaDB:

    
    
    sudo mysql_secure_installation

Durante a configuraçao, voce deve responder a uma serie de perguntas do
instalador:

    
    
    Enter current password for root (enter for none): (aperte enter)
    
    
    Set root password? [Y/n] y
    
    
    Remove anonymous users? [Y/n] y
    
    
    Disallow root login remotely? [Y/n] y
    
    
    Remove test database and access to it? [Y/n] y
    
    
    Reload privilege tables now? [Y/n] y

Depois de configurar o MariaDB, voce podera fazer o login no servidor de banco
de dados usando o usuario root do seu sistema Linux (nao sera atraves do
usuario root do MariaDB), usando Unix Socket:

    
    
    sudo mysql

Aproveite para criar um usuario administrador no MariaDB, que voce usara para
se conectar atraves do phpMyAdmin ou outros clientes. No prompt do MariaBD,
execute os tres comandos abaixo (desconsidere a parte antes do sinal >):

    
    
    MariaDB [(none)]> grant all privileges on *.* to usuario@localhost identified by 'senha_da_nasa';
    
    
    MariaDB [(none)]> flush privileges;
    
    
    MariaDB [(none)]> exit

* * *

#### Instalando o PHP

    
    
    sudo apt install php php-mysql php-mbstring libapache2-mod-php

* * *

#### Instalando o phpMyAdmin

    
    
    sudo apt install phpmyadmin

Fique atento as configuraçoes que aparecerao na tela (use as setinhas e a
tecla TAB para navegar nas opçoes, e use a barra de espaço para marcar alguma
opçao -- como na opçao do apache x lighttpd, por exemplo).

![](/img/1*4ww9RZnrNb6UlaWPiGDjYw.png)

Me perdoem pela cor horrivel, mas escolham o apache nessa tela

![](/img/1*nAsq9_ecJsDI1cZiWT8y0w.png)

Deixe na opçao sim para o dbconfig-common

![](/img/1*vqk2Rrk6i67iZslioDAghw.png)

Crie uma senha para o usuario phpmyadmin

Apos a configuraçao do phpMyAdmin, abra o navegador em
<http://localhost/phpmyadmin>

**ATEN ÇÃO**: use o usuario criado acima (na configuraçao do MariaDB, o que
tem a 'senha_da_nasa') para fazer o login no phpMyAdmin

![](/img/1*lRUvFHj8HJaaMz5XW-OvMQ.png)

Faça login com o usuario criado no MariaDB

Se tudo der certo, voce estara logado no phpMyAdmin e com permissao total de
administrador

![](/img/1*Hwo488G6vi7omeg1xJszWw.png)

Pagina inicial do phpMyAdmin

* * *

#### Conclusao

Como voce pode ver, eu nao usei o root do MariaDB para administrar o servidor
de banco de dados. Em vez disso, eu preferi deixar o root com o login usando
Unix Socket (meu root do Linux) e criar outro usuario administrador para fazer
login nos clientes de banco de dados.

As dicas acima funcionam para o MySQL Server tambem, a diferença e o nome do
pacote a ser instalado (mysql-server e nao mariadb-server).

Ate a proxima! Abraço.

