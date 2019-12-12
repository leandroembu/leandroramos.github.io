---
layout:	"post"
categories:	"blog"
title:	"Como instalar o MySQL no Ubuntu 18.04"
date:	2018-07-30
thumbnail:	/img/1*tuQwT4emzBkWBxg_IdrsJw.jpeg
author:	
---

* * *

![](/img/1*tuQwT4emzBkWBxg_IdrsJw.jpeg)

MySQL Logo

Se quiserem me doar um cafe pelo PagSeguro do UOL: <https://pag.ae/7Vu8Tt-pn>

MySQL e o gerenciador de bancos de dados de codigo aberto mais popular, neste
tutorial vamos mostrar como instala-lo numa maquina com o Ubuntu 18.04.

Traduçao/adaptaçao do artigo publicado no blog Linuxize:
<https://linuxize.com/post/how-to-install-mysql-on-ubuntu-18-04/>

* * *

#### Pre-requisitos

Antes de continuar, e importante que voce esteja logado com um usuario com
privilegios de root (sudo).

Atualize o sistema para obter a ultima versao dos pacotes:

    
    
    sudo apt update  
    sudo apt upgrade

#### Instale o MySQL no Ubuntu

Durante a elaboraçao deste tutorial, a versao mais atual do MySQL disponivel
no repositorio oficial do Ubuntu e a 5.7.

01- Instalando o MySQL

    
    
    sudo apt install mysql-server

02- Verificando a instalaçao do MySQL

Apos a instalaçao, o serviço MySQL se iniciara automaticamente. Para verificar
se o servidor esta rodando, digite:

    
    
    sudo systemctl status mysql
    
    
     _Exemplo da sa ida:_  
    ● mysql.service - MySQL Community Server  
       Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)  
       Active: active (running) since Wed 2018-06-20 11:30:23 PDT; 5min ago  
     Main PID: 17382 (mysqld)  
        Tasks: 27 (limit: 2321)  
       CGroup: /system.slice/mysql.service  
               `-17382 /usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid

03- Configurando o MySQL

Rode o comando mysql_secure_installation para configurar e melhorar a
segurança do seu servidor MySQL

    
    
    sudo mysql_secure_installation

Durante a configuraçao, voce tera a opçao [VALIDATE PASSWORD
PLUGIN](https://dev.mysql.com/doc/refman/5.6/en/validate-password.html), que e
usada para validar a força das senhas dos usuarios do MySQL. Existem tres
niveis de validaçao de força de senha: low (baixa), medium (media) e strong
(forte). Se voce nao quiser validar a força das senhas, apenas pressione
ENTER.

No proximo passo, voce podera alterar a senha do usuario root. Deixe em branco
e de ENTER (pois ele ainda nao possui senha), em seguida digite a senha
desejada.

Nas proximas questoes voce pode responder sim (Y) a todas (remover usuario
anonimo, remover acesso remoto, remover banco de dados de teste).

#### Faça login como root

Nos sistemas Ubuntu com o MySQL 5.7 (e posteriores), o usuario root usa o
metodo auth_socket para fazer o login, isso significa que voce nao conseguira
fazer o login com senha. Faça login usando seu superusuario do Linux:

    
    
    sudo mysql

Voce entrara no shell do MySQL, como o exemplo abaixo:

    
    
    Welcome to the MySQL monitor.  Commands end with ; or \g.  
    Your MySQL connection id is 8  
    Server version: 5.7.22-0ubuntu18.04.1 (Ubuntu)  
      
    Copyright (c) 2000, 2018, Oracle and/or its affiliates. All rights reserved.  
      
    Oracle is a registered trademark of Oracle Corporation and/or its  
    affiliates. Other names may be trademarks of their respective  
    owners.  
      
    Type 'help;' or '\h' for help. Type '\c' to clear the current input statement.

Se voce quiser fazer login como root atraves de programas externos, como o
phpMyAdmin, voce tem duas opçoes:

A primeira opçao e alterando o metodo de autenticaçao do usuario root:

    
    
     **ALTER** **USER** 'root'@'localhost' IDENTIFIED **WITH** mysql_native_password **BY** 'senha_da_nasa';
    
    
     **FLUSH** **PRIVILEGES** ;
    
    
    exit;

E a segunda opçao recomendada e criar um usuario administrativo com acesso a
todos os bancos de dados, sem alterar o metodo de autenticaçao do root:

    
    
     **GRANT** **ALL** **PRIVILEGES** **ON** *.* **TO** 'admin'@'localhost' IDENTIFIED **BY** 'senha_da_nasa';
    
    
    exit;

#### Conclusao

Podemos ver que a instalaçao do MySQL Server esta diferente, nao temos mais
aquele instalador que perguntava a senha de root e fazia a configuraçao
automaticamente, porem, podemos ver que nao e tao dificil configurar e deixar
o servidor rodando.

#### Fonte

Artigo traduzido/adaptado do blog Linuxize: <https://linuxize.com/post/how-to-
install-mysql-on-ubuntu-18-04/>

