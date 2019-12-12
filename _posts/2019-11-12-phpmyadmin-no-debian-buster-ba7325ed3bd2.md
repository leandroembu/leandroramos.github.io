---
layout:	"post"
categories:	"blog"
title:	"phpMyAdmin no Debian Buster"
date:	2019-11-12
thumbnail:	/img/0*23jwSa9AQXU1y_Sq.png
author:	
---

* * *

Este tutorial mostra a instalaçao manual do phpMyAdmin no Debian Buster (10) e
no Ubuntu Eoan (19.10), pois o pacote nao existe mais no repositorios dessas
versoes.

![](/img/0*23jwSa9AQXU1y_Sq.png)

Logo do phpMyAdmin

Para instalar os outros pacotes do LAMP, siga o tutorial que ainda funciona
nas versoes mais atuais dos sistemas Debian e Ubuntu --
<https://medium.com/@leandroembu/lamp-no-debian-
ubuntu-e-derivados-2019-7710ce29071f>

#### Importante

Nao existe (nunca existe) apenas uma forma de fazer as coisas no Linux, e vou
mostrar a forma com que eu consigo usar e manter o programa atualizado com
mais facilidade.

#### Instalando as dependencias

Vamos usar o Git para clonar o repositorio do phpMyAdmin no Github. Tambem
vamos usar o composer e o yarn para instalar as dependencias do phpMyAdmin
(voce pode instalar de outras formas, mas eu vou usar os pacotes do Debian).

    
    
    sudo apt install git composer yarnpkg php-xml php-curl php-zip

#### Repositorio Github do phpMyAdmin

Vamos clonar o repositorio em <https://github.com/phpmyadmin/phpmyadmin/> --
mas vamos usar o ramo (branch) STABLE, pois o master contem o codigo em
desenvolvimento.

![](/img/1*ro9AH7VAIVM4_7jCiYt9jg.png)

#### Clonando o repositorio

Escolha um diretorio (realmente pode ser onde voce quiser), eu farei o clone
dentro do diretorio do meu usuario

    
    
    git clone -b STABLE https://github.com/phpmyadmin/phpmyadmin.git

![](/img/1*et3bYaElTlcMWDKNe2cnUw.png)

Clonando o repositorio do phpMyAdmin

Entre na pasta do phpMyAdmin

    
    
    cd phpmyadmin

Use o composer para atualizar as dependencias

    
    
    composer update --no-dev

![](/img/1*3wCJf40dfiPUnjhJtCI8Pg.png)

Atualizando as dependencias com o composer

Use o yarn para instalar as dependencias do javascript

    
    
    yarnpkg install

Ou, se voce instalou o Yarn manualmente

    
    
    yarn install

![](/img/1*dGgngNLLLnMGQeNnEygDrQ.png)

Instalando as dependencias do javascript

#### Abrindo o phpMyAdmin

Crie um link simbolico no diretorio html do Apache -- ou onde quer que seu
webserver (nao somente o apache) tenha isso configurado -- apontando para a
pasta do phpmyadmin.

    
    
    sudo ln -s ~/phpmyadmin /var/www/html/phpmyadmin

Adapte o comando acima para a sua necessidade, caso o phpmyadmin nao esteja na
sua Home.

![](/img/1*W4XtXEQna7_ck_y0rHaihA.png)

Link apontando da pasta do Apache para a pasta do phpmyadmin

Abra seu navegador em localhost/phpmyadmin, ou no IP/nome do host onde estiver
seu servidor web. Faça o login no phpMyAdmin.

![](/img/1*nFFXF0YgkpYq0KA4y4aS5w.png)

Tela de login do phpMyAdmin

Seu phpMyAdmin esta pronto para ser usado

![](/img/1*sqfHg_FXqt3_-P0fTtiokQ.png)

Tela inicial do phpMyAdmin

#### Atualizando o phpMyAdmin

A vantagem de usar o Git para clonar o repositorio do phpMyAdmin e poder
atualizar o codigo do branch STABLE usando o comando git pull.

    
    
    git pull origin STABLE
    
    
    composer update --no-dev
    
    
    yarnpkg install

![](/img/1*DYRPMW9CDX4sl7XGjohW8w.png)

Atualizando o phpMyAdmin

#### Consideraçoes finais

Instalar o phpMyAdmin atraves do Git tem vantagens e desvantagens: eu gostei
de poder atualizar pela linha de comando, mas nao gostei do tamanho do
download do programa, mais de 700MB.

Uma outra forma de usar e baixar do site <https://www.phpmyadmin.net/> e
substituir o download por uma versao mais nova quando desejar.

Pessoalmente, nao uso o phpMyAdmin. Para administrar usuarios, permissoes e
outras coisas eu acabo usando a linha de comando, e para criar bancos de dados
e tabelas uso outras ferramentas, como o DBeaver. Mas e bom saber lidar com o
phpMyAdmin porque **ele e muito usado em sistemas de hospedagem, e as vezes
nao temos acesso a partir de outros hosts ou via ssh ao servidor**.

Referencia: <https://docs.phpmyadmin.net/en/latest/setup.html#installing-from-
git>

Deixem comentario, me corrijam, deem sugestoes, etc. Um grande abraço e ate a
proxima!

