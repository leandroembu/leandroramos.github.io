---
layout:	"post"
categories:	"blog"
title:	"phpMyAdmin + Servidor embutido do PHP"
date:	2018-08-17
thumbnail:	/img/1*9tY-QRgJZWgu-bSq6CyiSw.png
author:	
---

* * *

![](/img/1*9tY-QRgJZWgu-bSq6CyiSw.png)

O [phpMyAdmin](https://www.phpmyadmin.net/) e um dos clientes de
[MySQL](https://www.mysql.com/)/[MariaDB](https://mariadb.org/) mais populares
do mundo, facilmente encontrado em quase todos os servidores que hospedem PHP.

Em servidores, o phpMyAdmin e usado em conjunto com os servidores web Apache e
Nginx, entre outros. No entanto, no seu ambiente de desenvolvimento, voce pode
usar o [servidor
embutido](https://secure.php.net/manual/pt_BR/features.commandline.webserver.php)
do PHP para rodar o phpMyAdmin. Veja como fazer:

#### Requisitos:

  * PHP a partir da versao 5.4 (preferencialmente a partir da versao 7, pois "pra frente e que se anda");
  * MySQL Server ou MariaDB Server
  * Funciona no Linux, no Windows, Mac, Unix e desconfio que em outros sistemas que nao conheço.

#### Obtendo o phpMyAdmin:

Faça o download do phpMyadmin e descompacte em qualquer pasta do seu
computador (isso mesmo, nao precisa ser na /var/www/whatever):

Versao atual na data em que escrevi o artigo:
<https://files.phpmyadmin.net/phpMyAdmin/4.8.2/phpMyAdmin-4.8.2-all-
languages.zip>

Para outras versoes: <https://www.phpmyadmin.net/downloads/>

#### Configurando o phpMyAdmin:

1- Descompacte o arquivo baixado

2- Entre na pasta `phpMyAdmin-4.8.2-all-languages` (renomeie para `phpmyadmin
`se achar conveniente)

3- Abra o arquivo config.sample.inc.php, salve-o como config.inc.php e
configure a variavel `$cfg['Servers'][$i]['host'] = 'localhost';` com o IP ou
nome do seu host.

4- Abra o terminal e digite:

    
    
    php -S localhost:8080

  * O numero da porta pode ser diferente

6- Abra o navegador em <http://localhost:8080>

![](/img/1*BaK_nltB-227j7haO1KjQA.png)

#### Conclusao:

Este artigo foi uma breve introduçao do que voce pode fazer com o servidor
embutido do PHP, e uma mostra de que voce pode usar o phpMyAdmin mesmo se ele
nao estiver disponivel no repositorio de sua distribuiçao Linux, isso ajuda a
desmistificar um pouco a necessidade de instalar pacotes e a entender que
alguns pacotes sao apenas scripts PHP dentro de uma pasta.

Por favor, me avisem se tiver algo errado no artigo.

Ate a proxima, pessoal!

