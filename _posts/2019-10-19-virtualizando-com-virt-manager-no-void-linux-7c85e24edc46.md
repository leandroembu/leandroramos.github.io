---
layout:	"post"
categories:	"blog"
title:	"Virtualizando com virt-manager no Void Linux"
date:	2019-10-19
thumbnail:	/img/1*um9UR4A8rTijEyT344eDqA.png
author:	
---

* * *

![](/img/1*um9UR4A8rTijEyT344eDqA.png)

Depois de muito tempo eu voltei a usar o Void Linux no meu modesto notebook.
Para recomeçar a falar sobre o sistema, farei um pequeno tutorial de
instalaçao do Virt Manager, gerenciador de maquinas virtuais usando KVM ou
qemu-kvm.

* * *

#### Instalando os pacotes necessarios

Instale os pacotes virt-manager e qemu, pois as dependencias necessarias ja
virao na instalaçao. Use o xbps-install para isso:

    
    
    sudo xbps-install virt-manager qemu

![](/img/1*an89SxNucU8Bbm8JoZKYaA.png)

Instalaçao dos pacotes necessarios

#### Habilitando e iniciando os serviços

Inicie os tres serviços necessarios para o uso do virt-manager

    
    
    sudo ln -s /etc/sv/libvirtd /var/service  
    sudo ln -s /etc/sv/virtlockd /var/service  
    sudo ln -s /etc/sv/virtlogd /var/service

#### Verificando o status dos serviços

    
    
    sudo sv status libvirtd   
    sudo sv status virtlogd   
    sudo sv status virtlockd

![](/img/1*6UUSB0GYIOXRD8yXbLhViw.png)

Status dos serviços de virtualizaçao

#### Criando a primeira maquina virtual

Abra o programa virt-manager e clique no botao + para adicionar uma maquina
virtual

![](/img/1*HrcWhqvfRiV1YLmloLtv3Q.png)

Tela principal do virt-manager

![](/img/1*BDXs8aYm1y08j-GlzbnkJA.png)

Adicionando uma maquina virtual

![](/img/1*BcgmvY4H4X1z8fxC8MLUgQ.png)

Clique em "Navegar" para escolher o arquivo ISO

![](/img/1*6M6sJKZSGL7G6dcMxGnRWg.png)

Em "Navegar Localmente", procure a pasta onde esta o arquivo ISO desejado

![](/img/1*6_KPIO8a39EgwTqx5UEeQA.png)

Selecione o sistema desejado. Caso nao o encontre na lista, escolha Generic

![](/img/1*4vA4L-HeAVbwv9jf_wzNIw.png)

Alocaçao de memoria em MB e nucleos do processador

Os discos virtuais ficam, por padrao, no diretorio /var. Se voce possui a
partiçao /home separada, indique o caminho personalizado no campo de texto.

![](/img/1*kz9PKEUbGbNK-ZvKWkeg7Q.png)

Indique o tamanho do disco virtual

![](/img/1*o-R_Kqz3NVpb_YEqT9St0A.png)

De um nome a maquina virtual e marque a opçao "Personalizar a configuraçao
antes da instalaçao"

Em "CPUs", marque a opçao "Copiar configuraçao da CPU do host", e a melhor
opçao se voce for iniciante.

![](/img/1*WEuP0Og2BUsqlR0IAOZgeA.png)

Opçoes gerais da maquina virtual

#### Iniciando a instalaçao da maquina virtual

Apos as configuraçoes da maquina, clique em "Iniciar Instalaçao". Nos proximos
artigos (ou videos acompanhados de artigos) eu falarei mais sobre o virt-
manager.

![](/img/1*SDna6trRfU1s38htWl_OQw.png)

Live system do Kubuntu 18.04 rodando no virt-manager do Void Linux

Obrigado pela leitura. Ate a proxima, pessoal!

