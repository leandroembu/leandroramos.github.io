---
layout:	"post"
categories:	"blog"
title:	"Instalando o Google Chrome no Void Linux, usando o xbps-src"
date:	2018-08-15
thumbnail:	/img/1*VjwiqZEHKgI0EcS4hDvfHA.png
author:	
---

* * *

![](/img/1*VjwiqZEHKgI0EcS4hDvfHA.png)

O Void Linux possui uma ferramenta para criaçao de pacotes a partir de
binarios de terceiros, e tambem a partir de codigos-fonte, chamada [xbps-
src](https://wiki.voidlinux.eu/Xbps-src), que se assemelha aos Slackbuilds do
Slackware, PKGBUILD do Archlinux e EBUILD do Gentoo. Neste artigo vou mostrar
como começar a usar os xbps-src, usando o Google Chrome como exemplo.

* * *

### Requisitos:

Precisamos instalar algumas dependencias antes de usarmos o xbps-src:

    
    
    sudo xbps-install git base-devel xtools

### Clone do repositorio void-packages:

    
    
    git clone https://github.com/void-linux/void-packages

### Instalaçao do bynary-bootstrap

Para trabalhar com os templates do xbps-src (pode conferi-los na pasta ~/void-
packages/srcpkgs/nomeDoPacote/template), precisamos configurar o binary-
bootstrap:

    
    
    cd void-packages  
    ./xbps-src binary-bootstrap

Tambem precisamos permitir pacotes restritos (para o caso do Google Chrome):

    
    
    echo XBPS_ALLOW_RESTRICTED=yes >> ~/void-packages/etc/conf

### Construindo o pacote .xbps

Agora podemos construir (build) nosso pacote .xbps:

    
    
    ./xbps-src pkg google-chrome

Reparem que o template utiliza o pacote .deb para construir nosso .xbps

### Instalando o pacote

Finalmente, podemos instalar nosso pacote usando o xbps-install:

    
    
    sudo xbps-install --repository=/home/seu-usuario/void-packages/hostdir/binpkgs/nonfree google-chrome

E pronto! Podemos usar o Google Chrome no Void, graças ao maravilhoso xbps-
src.

Nos proximos artigos mostrarei como construir pacotes .xbps a partir de
codigo-fonte e tambem como atualizar os pacotes instalados atraves do xbps-
src.

Link para o screencast do tutorial: <https://youtu.be/pk-HaPbw4vU>

Ate a proxima, pessoal!

