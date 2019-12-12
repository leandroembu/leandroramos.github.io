---
layout:	"post"
categories:	"blog"
title:	"Usando apps Electron no meu notebook de supermercado — Parte I"
date:	2019-11-12
thumbnail:	/img/0*rUJtADPD1NitnI6K.png
author:	
---

* * *

![](/img/0*rUJtADPD1NitnI6K.png)

Logo do Electron

#### Minha maquina

  * Acer Travelmate B117M
  * Celeron N3060 Dual Core (1.5-2.4GHz)
  * RAM: 4GB DDR3
  * SSD: Kingston A400 240GB -- NVME

Costumo chamar minha maquina de "notebook de supermercado", por ter uma
configuraçao parecida com as maquinas populares vendidas no Brasil. Mesmo
assim, e uma maquina bem agil para fazer o meu trabalho, inclusive para fazer
screencasts para o meu canal no YouTube, mas uso ferramentas nativas leves,
como os editores Vim e Geany, IDE QtCreator (que apesar de muito poderoso e
bem leve, e multiplataforma -- existe multiplataforma alem de Electron e
Java). Uso ambientes desktop leves como XFCE e LXDE e lido com muitas coisas
pela linha de comando.

#### Meu sistema operacional

  * Debian Sid
  * LXDE
  * Swapfile de 4GB (pois uso maquinas virtuais)

#### Proposta

Passar alguns dias ou semanas usando programas desenvolvidos com Electron JS

#### Objetivo

Verificar se programas Electron sao usaveis em maquinas populares

#### Programas a serem usados

  * Rambox -- para meus chats, GMail e Twitter

![](/img/1*xKyD6LZjWvani8xFs_5RBA.png)

Rambox

  * VSCodium -- Para fazer algum codigo

![](/img/1*2ptQywmwiUrZo3AnSOSdvA.png)

VSCodium, vamos codar

  * Cerebro -- launcher para programas, arquivos e buscas na web (entre outras coisas)

![](/img/1*uiy5PRmCigvhBs3Se3uFww.png)

Cerebro

  * Hyper -- emulador de terminal (sim, um emulador de terminal…)

![](/img/1*gEgN-pmxZeNhYpslKF8gAg.png)

Hyper -- Emulador de Terminal

  * GitKraken -- cliente GUI para Git

![](/img/1*C5R75lX8CriiKQozrTKslQ.png)

GitKraken, um jeito bonitinho de lidar com Git

  * AppServer -- Desktop Proxy & App Server para HTML e MD

![](/img/0*DWhkZRtUSSXyJfK1.png)

Ainda nao consegui fazer o deploy do app no meu notebook

  * Balena Etcher -- Utilitario para gerar pendrives bootaveis

![](/img/1*JT2Kgm3vGluDeLOFuRaLtg.png)

Balena Etcher, um dd bonitinho

  * Colorpicker -- Utilitario desktop para seleçao de cores

![](/img/1*vgd-f81D-t85b6s_5C64jw.png)

Colorpicker

  * Piqture -- Ferramenta de screenshots

![](/img/1*znHzccr5GHHxohzKJTrjjw.png)

Piqture, screenshots

#### Tamanho dos downloads

  * Cerebro: AppImage com 54,9MB
  * Rambox: AppImage com 83,2MB
  * Codium: Repositorio deb de Paul Carroty -- 58,7MB
  * Hyper: Pacote .deb com 37,4MB
  * GitKraken: Pacote .deb com 74,1MB
  * AppServer: Repositorio Git com 1MB
  * Balena Etcher: Pacote Zip com 81,1MB
  * Colorpicker: AppImage com 50,2MB
  * Piqture: Pacote Zip com 126MB

#### Instalaçao dos programas

A instalaçao dos programas foi facil. Exceto o Balena Etcher, os appimages se
integraram ao sistema, mas o Balena Etcher nao precisa disso porque e usado
poucas vezes.

Os pacotes em zip tambem foram faceis de usar, alguns eram binarios e outros
eram appimages dentro do arquivo zip.

Os pacotes .deb funcionaram sem problemas no Debian Sid, bastou instala-los
com o APT.

#### Fim da parte I

Na Parte II vou falar sobre o uso do meu notebook com os apps Electron no
lugar dos apps nativos, incluindo emulador de terminal, Telegram Desktop,
lançador de programas, editor de textos e ferramenta de screenshot.

Se tiverem sugestoes de apps ou dicas para fazer um bom uso da minha maquina
com esses apps, deixem nos comentarios. Abraços!

