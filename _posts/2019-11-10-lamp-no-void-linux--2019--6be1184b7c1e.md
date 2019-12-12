---
layout:	"post"
categories:	"blog"
title:	"LAMP no Void Linux (2019)"
date:	2019-11-10
thumbnail:	/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg
author:	
---

* * *

![](/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg)

Fonte da imagem -- <https://www.unixmen.com/how-to-install-lamp-stack-
ubuntu-17-04/>

Ola, pessoal. Beleza?

Vou fazer a ediçao 2019 da instalaçao do LAMP no Void Linux, pois algumas
coisas mudaram, entre elas o pacote phpmyadmin que agora esta disponivel no
repositorio da distribuiçao.

#### Instalando os pacotes necessarios

    
    
    sudo xbps-install -S php-apache php-mysql apache mariadb phpMyAdmin

![](/img/1*gojqxn0pKGt0QZD10EToXQ.png)

Hoje eu substitui o DBeaver pelo phpMyAdmin.

#### Habilitando os serviços do Apache e do MariaDB e configurando o MariaDB

    
    
    sudo ln -s /etc/sv/apache /var/service/apache  
    sudo ln -s /etc/sv/mysqld /var/service/mysqld
    
    
    mysql_secure_installation

Depois de setar suas configuraçoes do MariaDB, voce pode fazer o login:

    
    
    mysql -uroot -p

Pode testar o Apache no navegador tambem em <http://localhost>

![](/img/1*MM_AOSaCl8GPq8kY9ed6IQ.png)

Tela inicial do Apache no Void Linux

#### Habilitando o modulo do PHP no Apache

Edite o arquivo /etc/apache/httpd.conf:

Comente a linha do modulo mpm_event_module (coloque um # no começo da linha) e
descomente a linha do modulo mpm_prefork_module (remova # do começo da linha),
vai ficar assim:

    
    
    #LoadModule mpm_event_module modules/mod_mpm_event.so  
    LoadModule mpm_prefork_module modules/mod_mpm_prefork.so

![](/img/1*5IHENvW7QB7upLazue2T3g.png)

No final da seçao de LoadModule, coloque as linhas que carregam o modulo do
PHP:

    
    
    LoadModule php7_module /usr/libexec/httpd/modules/libphp7.so  
    AddHandler php7-script .php

![](/img/1*RoYbN9NhJreboSWiL0s1pw.png)

No final do arquivo, coloque a linha abaixo:

    
    
    Include /etc/apache/extra/php7_module.conf

![](/img/1*El1bQ96N4RCvLMWl-cCKHw.png)

Reinicie o serviço do Apache:

    
    
    sudo sv restart apache

Com isso, o PHP ja sera interpretado pelo Apache.

#### Configurando o PHP para trabalhar com o MariaDB

Edite o arquivo /etc/php/php.ini e descomente a linha (remova o ; do inicio da
linha):

    
    
    extension=mysqli

![](/img/1*I9pyTocHMFJmxOFR6V87eA.png)

#### Configurando o phpMyAdmin

O phpMyAdmin fica no diretorio /usr/share/webapps/phpMyAdmin. Podemos
configurar o Apache para abri-lo a partir do caminho citado, mas eu prefiro
uma soluçao mais simples: fazer um link simbolico no diretorio do Apache,
apontando para o diretorio do phpMyAdmin.

    
    
    sudo ln -s /usr/share/webapps/phpMyAdmin /srv/www/apache/phpmyadmin

Abra seu navegador na URL <http://localhost/phpmyadmin>

![](/img/1*Iu5WR996PEW2yC_vlsHVrQ.png)

Tela de login do phpMyAdmin

Faça o login com sua senha de root (ou outro usuario criado no MariaDB)

![](/img/1*WO09czGaa7x4ZKLHa_G-Vw.png)

phpMyAdmin pronto para ser usado

Muito obrigado pela leitura. Ate a proxima, pessoal!

