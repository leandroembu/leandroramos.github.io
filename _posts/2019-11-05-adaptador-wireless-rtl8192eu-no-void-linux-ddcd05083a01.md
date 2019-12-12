---
layout:	"post"
categories:	"blog"
title:	"Adaptador Wireless RTL8192EU no Void Linux"
date:	2019-11-05
thumbnail:	/img/1*ORZWXyKN28geoUNLXxhntA.png
author:	
---

* * *

![](/img/1*ORZWXyKN28geoUNLXxhntA.png)

Void Linux com XFCE

O adaptador wireless TP-LINK TL-WN821N nao e reconhecido apropriadamente em
quase nenhuma distribuiçao Linux, nem mesmo no Ubuntu e derivados. Adaptei os
passos de instalaçao de <https://github.com/Mange/rtl8192eu-linux-driver> para
funcionarem no Void Linux (pois o original foi feito para Debian/Ubuntu).

 **Nota importante:** vou usar _sudo_ para fazer os passos a seguir, pois n ao
tenho o costume (e desencorajo as pessoas a terem o costume) de usar o login
de root para tudo.

* * *

#### Instale as dependencias

    
    
    sudo xbps-install git linux-headers base-devel dkms

#### Clone o repositorio do driver

    
    
    git clone <https://github.com/Mange/rtl8192eu-linux-driver>

#### Entre no diretorio do driver

    
    
    cd rtl8192eu-linux-driver

#### Adicione o driver ao DKMS

 **Aten çao:** repare no ponto (.) no final do comando abaixo

    
    
    sudo dkms add .

![](/img/1*S2IGA_AlY10yo05tCU5xVw.png)

#### Compile e instale o driver com o DKMS

    
    
    sudo dkms install rtl8192eu/1.0

![](/img/1*wyx4I_g27ywYfpO-Qk_Yqw.png)

#### Impeça que o driver generico seja carregado na inicializaçao

    
    
    echo "blacklist rtl8xxxu" | sudo tee /etc/modprobe.d/rtl8xxxu.conf

#### Crie o diretorio para o novo modulo a ser carregado com o kernel

    
    
    sudo mkdir /etc/modules-load.d

#### Coloque o novo modulo para ser carregado com o kernel

    
    
    echo -e "8192eu\n\nloop" | sudo tee /etc/modules-load.d/rtl8192eu.conf

#### Atualize o GRUB

    
    
    sudo update-grub

![](/img/1*g58IZK9GhOdyi9tmlnczdg.png)

#### Atualize o initramfs com o Dracut

    
    
    sudo dracut --force

![](/img/1*47NI6UM_Hc4JtNWWdOzQKQ.png)

#### Reinicie o sistema

    
    
    sudo reboot

#### Consideraçoes finais

Se tiverem alguma duvida ou encontrarem erros no tutorial, por favor, me
avisem nos comentarios. Abraços!

