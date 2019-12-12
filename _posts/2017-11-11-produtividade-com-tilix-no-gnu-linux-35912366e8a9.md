---
layout:	"post"
categories:	"blog"
title:	"Produtividade com Tilix no GNU/Linux"
date:	2017-11-11
thumbnail:	/img/1*3Ds0rAYCO27Q6d3GY8uLgg.png
author:	
---

* * *

Se quiserem me doar um cafe pelo PagSeguro do UOL: <https://pag.ae/7Vu8Tt-pn>

[Tilix](https://gnunn1.github.io/tilix-web/) e um emulador de terminal com o
recurso de _tile_ , _ou split_ , que permite dividirmos a tela em varias
colunas e linhas, facilitando a execuçao de varias tarefas na mesma janela.

![](/img/1*3Ds0rAYCO27Q6d3GY8uLgg.png)

Tilix rodando no Xubuntu 17.10

#### Instalando o Tilix

Instalar o Tilix e bem simples na maioria das distribuiçoes GNU/Linux. Veja
como instalar no Ubuntu e no Fedora (distribuiçoes que eu mais uso):

No Fedora 26 (ou 27): `$ sudo dnf install tilix  
`No Ubuntu 16.04 (e posteriores): `$ sudo apt install tilix  
`Voce tambem pode instalar a partir da Central de Programas da sua
distribuiçao.

#### Usando o Tilix

![](/img/1*OtOLjM5_e2Cax-62OO5_TA.png)

Janela de opçoes do Tilix

A sessao padrao do Tilix se inicia com uma janela simples, como qualquer outro
emulador de terminal.

Na janela de opçoes e possivel ver e alterar os atalhos de teclado e
configurar o comportamento do programa.

![](/img/1*z0wiuiyjQpWnkKMWWrTZ5Q.png)

CTRL+Alt+R abre uma nova janela a direita

Usando o atalho padrao CTRL+Alt+R, uma nova janela se abre a direita, o que
tambem pode ser feito com o botao direito do mouse em qualquer regiao da tela
atual.

![](/img/1*GIdCqJCqcM8qAaB_zMxlBA.png)

CTRL+Alt+D abre uma nova janela abaixo

Usando o atalho padrao CTRL+Alt+D, uma nova janela se abre abaixo da janela
atual. Alterei meu atalho para CTRL+Alt+G porque o D serve para mostrar a area
de trabalho no meu XFCE. Para alternar entre as janelas, o atalho mais pratico
e Alt+Setas de direçao.

Para maximizar/restaurar uma das janelas, o atalho padrao e CTRL+Shift+x.

![](/img/1*JCgluMAy402wLe5SrwKqWw.png)

Vim, PHP Server, Htop e Links Browser. Rodando Hello World PHP

Voce pode abrir quantos tiles quiser. Eu uso um para o Vim, outro para rodar o
servidor web ou olhar algum log e um para navegar pelo resultado, seja no
console ou no navegador CLI (Links). _CLI = Command Line Interface_

![](/img/1*crOvW3yIhEbNJGoaIv9kZg.png)

Tilix no modo Quake

O Tilix tambem possui um "Quake Mode", que abre no topo da tela com efeito
dropdown, mas so se torna produtivo se configurarmos um atalho de teclado para
o comando `tilix --quake.`Para essa funçao eu escolheria outro emulador, como
o Guake (dos aplicativos Gnome) ou o Yakuake (dos aplicativos KDE).

Quem usa GNU/Linux por algum tempo sempre acaba usando (e gostando de usar) o
terminal. O Tilix me ajuda bastante enquanto desenvolvo software, escrevo
documentaçao ou qualquer outra tarefa que eu prefira fazer no terminal. Vale
lembrar que o Tilix e uma aplicaçao de ambiente grafico, portanto nao roda no
modo texto (servidores, por exemplo). Uma excelente opçao para quem trabalha
em modo texto e o [Tmux](https://github.com/tmux/tmux/wiki), que eu uso em
servidores.

Existem muitos emuladores de terminal fantasticos ([ZSH](http://www.zsh.org/),
[Fish](https://fishshell.com/), [Hyper](https://github.com/zeit/hyper),
[Terminator](https://github.com/albfan/terminator), e
[outros](https://en.wikipedia.org/wiki/List_of_terminal_emulators#Linux)), e
todos eles possuem caracteristicas que podem aumentar sua produtividade. Minha
escolha, sempre que possivel, e o Tilix.

Este foi meu primeiro post no Medium, espero que possa ser util. Sinta-se a
vontade para comentar, compartilhar, sugerir, etc.

Obrigado por ler o post.

