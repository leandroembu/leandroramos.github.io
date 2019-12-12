---
layout:	"post"
categories:	"blog"
title:	"Fedora Silverblue 31 no meu Atom com 2GB de RAM"
date:	2019-12-03
thumbnail:	/img/1*YkdB3uotgPx3YivDHIIyWA.png
author:	
---

* * *

Antes de começar: façam meu natal mais feliz. Se meu conteudo ajuda de alguma
forma, considere fazer uma doaçao no link
[https://pagseguro.uol.com.br/checkout/nc/nl/donation/sender-
identification.jhtml?t=7b3d14829771610a94a20d898133a3caa2f81e757e2ba2726161f9eaf50981a4&e=true](https://pagseguro.uol.com.br/checkout/nc/nl/donation
/sender-
identification.jhtml?t=7b3d14829771610a94a20d898133a3caa2f81e757e2ba2726161f9eaf50981a4&e=true)

![](/img/1*YkdB3uotgPx3YivDHIIyWA.png)

Fedora Silverblue -- Kinoite XFCE

Recentemente, fiz um [post](https://medium.com/@leandroembu/minha-experi%C3
%AAncia-com-o-fedora-silverblue-1e2c37cc14ae) relatando minha exteriencia com
o Fedora Silverblue XFCE no meu super PC com processador Atom e 2GB de RAM.

Na ocasiao, eu tive problemas para instalar a versao 31, e relatei o erro no
post, mas resolvi instalar a versao 31 novamente e fazer a coisa funcionar.

#### Resoluçao do problema

Ao instalar o Fedora Silverblue 31 no meu Atom, o gerenciador de display GDM
nao funcionou, mas o utilitario para a criaçao do usuario funcionou, o _gnome-
initial-setup_ , e apos a criaçao do usuario eu usei a linha de comando (TTY)
para me conectar a internet e instalar o XFCE usando o projeto Kinoite, usando
o tutorial do blog FastOS Linux: <https://fastoslinux.com/2019/07/30
/silverblue-com-kde-plasma/> (adaptando o tutorial para instalar o XFCE e nao
o KDE Plasma).

![](/img/0*5udEwtmw3tb4zOVd.png)

Criando o usuario com o gnome-initial-setup

![](/img/0*VdhgydKk3wUlReWp.png)

Criando o usuario com o gnome-initial-setup

![](/img/0*BYUV2mCZd6myPk2V.jpg)

Erro na sessao do GNOME

Apos a criaçao do usuario, acessei o TTY (CTRL+ALT+F2) e usei a ferramenta
_nmcli_ para me conectar  a internet.

Mostrando as conexoes disponiveis

    
    
    [leandro@fedora]$ nmcli c show  
    NAME    UUID                                 TYPE   DEVICE   
    Leandro 779cd78a-8c6d-44de-abe7-b75cd0a2b710 wifi   wlp0s29f7u8   
    enp1s0 6814aadf-f46d-4900-8f20-728052eda756  ethernet --

Apagando a conexao wifi _Leandro_ para limpar as configura çoes

    
    
    [leandro@fedora ~]$ nmcli c delete Leandro

Configurando a conexao _Leandro_

    
    
    [leandro@fedora]$ nmcli device wifi connect Leandro password minha-senha

Depois de configurar a conexao, segui o tutorial do FastOS e instalei o
ambiente XFCE pelo TTY, assim como fiz na versao 30 no outro
[post](https://medium.com/@leandroembu/minha-experi%C3%AAncia-com-o-fedora-
silverblue-1e2c37cc14ae).

#### Usando meu novo sistema

Apos a instalaçao do ambiente XFCE, o sistema iniciou normalmente e o gestor
de display LightDM iniciou sem erro. Agora posso aproveitar meu novo sistema
leve e com um ambiente que estou bem acostumado.

O Fedora Silverblue esta prestes a se tornar meu Fedora padrao, estou gostando
muito do sistema.

![](/img/1*R9UHdd9iA8ABjStZ8QV7zg.png)

Fedora Silverblue 31 com XFCE 4.14 instalado com sucesso

