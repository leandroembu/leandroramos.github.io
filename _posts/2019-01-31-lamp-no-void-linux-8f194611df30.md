---
layout:	"post"
categories:	"blog"
title:	"LAMP no Void Linux"
date:	2019-01-31
thumbnail:	/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg
author:	
---

* * *

![](/img/1*-YNY3KLuXt6HIR7h-eIcow.jpeg)

Fonte da imagem -- <https://www.unixmen.com/how-to-install-lamp-stack-
ubuntu-17-04/>

Ola, pessoal. Beleza?

Vou mostrar como eu faço para instalar a pilha LAMP no Void Linux. O processo
e parecido com o de outras distros, mas muitos podem ter duvidas, vamos ao que
interessa!

#### Instalando os pacotes necessarios

    
    
    sudo xbps-install -S php-apache php-mysql apache mariadb dbeaver

Reparem que eu instalei o [DBeaver](https://dbeaver.io), gosto muito desse
cliente de bancos de dados.

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

No final da seçao de LoadModule, coloque as linhas que carregam o modulo do
PHP:

    
    
    LoadModule php7_module /usr/libexec/httpd/modules/libphp7.so  
    AddHandler php7-script .php

No final do arquivo, coloque a linha abaixo:

    
    
    Include /etc/apache/extra/php7_module.conf

Reinicie o serviço do Apache:

    
    
    sudo sv restart apache

Com isso, o PHP ja sera interpretado pelo Apache.

#### Configurando o PHP para trabalhar com o MariaDB

Edite o arquivo /etc/php/php.ini e descomente a linha (remova o ; do inicio da
linha):

    
    
    extension=mysqli

#### Instalando o phpMyAdmin

Na verdade, o phpMyAdmin nao sera "instalado", sera baixado do site do
desenvolvedor -- <https://www.phpmyadmin.net/downloads/> -- e sera
descompactado e colocado na pasta do Apache.

Baixe o arquivo (link acima), descompacte, renomeie a pasta para phpmyadmin e
copie para a pasta do apache. Use o terminal ou o gerenciador de arquivos
(desde que tenha permissoes de root).

    
    
    sudo cp -r phpmyadmin /srv/www/apache/

Abra seu navegador na URL <http://localhost/phpmyadmin>

#### Video (veja na pratica):

#### Conclusao

Apos seguir os passos acima, seu ambiente de desenvolvimento com a pilha LAMP
devera estar funcionando. A diferença entre a instalaçao que fiz no Void das
outras distrivuiçoes Linux que uso e que o phpMyAdmin nao e empacotado nos
repositorios do Void, nem no void-packages (xbps-src). Mas nao importa, pois o
phpMyAdmin e um "site" que so precisa ser executado pelo servidor web + php.

Se quiser ver como eu uso o phpMyAdmin com o servidor embutido do PHP, sem
Apache ou Nginx, veja o outro [artigo](https://medium.com/@leandroembu
/phpmyadmin-servidor-embutido-do-php-a97c51c7c97f).

Um abraço e ate a proxima, pessoal!

