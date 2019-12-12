---
layout:	"post"
categories:	"blog"
title:	"Desabilitando serviços no Void Linux"
date:	2019-11-10
thumbnail:	/img/0*D8dq7Elbq5uYq3WM.png
author:	
---

* * *

![](/img/0*D8dq7Elbq5uYq3WM.png)

Logo do Void Linux

Quando habilitamos um serviço no Void Linux, ele passa a iniciar junto com o
sistema. Mas existem alguns serviços que voce nao gostaria de ter habilitados
em toda inicializaçao. Vou falar um pouco sobre isso aqui.

#### Habilitando um serviço

Para exemplificar a habilitaçao de um serviço eu vou usar o Apache. Apos a
instalaçao do pacote apache, podemos habilita-lo criando um link simbolico no
diretorio /var/services, apontando para o serviço que fica em /etc/sv.

    
    
    sudo ln -s /etc/sv/apache /var/service/apache

Com o comando acima, o serviço sera iniciado imediatamente, e tambem toda vez
que voce iniciar a maquina.

No diretorio /etc/sv temos os serviços disponiveis no sistema, mas nao
necessariamente habilitados.

![](/img/1*tqS7sjcvLL1UuIXMGr3xwA.png)

Serviços disponiveis, mas nao habilitados

No diretorio /var/service temos os serviços habilitados, ou que vao iniciar
junto com o sistema.

![](/img/1*TjX8cBtk9pjCP2LC7uRv5Q.png)

Serviços habilitados

#### Desabilitando um serviço

Nao existe apenas uma forma de desabilitar um serviço, e voce deve ver a forma
que atende melhor as suas necessidades.

#### Iniciando um serviço sem deixa-lo ativo

Para fazer com que o serviço apache inicie junto com o sistema, mas sem estar
ativo (down), voce pode criar um arquivo vazio, com o nome **_down_** , dento
do diretorio /etc/sv/apache/

    
    
    sudo touch /etc/sv/apache/down

![](/img/1*pC6YzJbz81hqFXP3Oe8rhA.png)

Criando o arquivo down em /etc/sv/apache/

Ao ver o status do serviço, voce vai reparar que ele tem um "normally down" no
fim da linha do status. Isso indica que o serviço vai iniciar no estado
**_down_** , ou seja, nao estara rodando de fato. O serviço vai iniciar com o
sistema, mas inativo.

    
    
    sudo sv status apache

![](/img/1*fog-QHzNewFZbtzyG7gyKg.png)

Serviço rodando, mas indicando que normalmente inicia inativo

Ao reiniciar o sistema, o serviço estara inativo, e voce podera inicia-lo com
o comando abaixo:

    
    
    sudo sv start apache

#### Desabilitando o serviço de forma definitiva

Se voce quiser simplesmente nunca mais usar o serviço, pode apagar o link
simbolico de /var/service (e provavelmente voce vai querer, tambem,
desinstalar o pacote).

    
    
    sudo rm /var/service/apache

![](/img/1*ymarzQQe8Cz-nnE6F1Q0rQ.png)

Removendo, definitivamente, o serviço

#### Removendo o pacote

Se voce removeu o serviço e nao quer mais ter o pacote no seu sistema, basta
remove-lo.

    
    
    sudo xbps-remove apache

Aproveite para remover os pacotes orfaos tambem, e tambem os pacotes obsoletos
no cache do sistema

    
    
    sudo xbps-remove -oO #o para os orfaos e O para os obsoletos

E e isso. Muito obrigado pela leitura. Ate a proxima, pessoal!

