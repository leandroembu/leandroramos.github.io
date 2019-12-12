---
layout:	"post"
categories:	"blog"
title:	"Minha experiência com o Fedora Silverblue"
date:	2019-11-29
thumbnail:	/img/1*ffmx7m6g_xlZeuTJzGeR5w.png
author:	
---

Veja como esta sendo minha experiencia com um sistema moderno em um computador
muito fraco e antigo.

* * *

Antes de começar: façam meu natal mais feliz. Se meu conteudo ajuda de alguma
forma, considere fazer uma doaçao no link
[https://pagseguro.uol.com.br/checkout/nc/nl/donation/sender-
identification.jhtml?t=7b3d14829771610a94a20d898133a3caa2f81e757e2ba2726161f9eaf50981a4&e=true](https://pagseguro.uol.com.br/checkout/nc/nl/donation
/sender-
identification.jhtml?t=7b3d14829771610a94a20d898133a3caa2f81e757e2ba2726161f9eaf50981a4&e=true)

![](/img/1*ffmx7m6g_xlZeuTJzGeR5w.png)

Tela de detalhes do sistema e do PC

Silverblue e o novo nome do sistema operacional conhecido anteriormente como
_Atomic Workstation_ , e seus principais beneficios sao velocidade, segurança
e base imutavel. Se quiserem saber mais sobre o que e o Fedora Silverblue,
leiam [aqui](https://fedoramagazine.org/what-is-silverblue/).

#### Meu "super" hardware

  * PC Desktop NeoPC de 2011
  * Processador: Intel Atom D525 Dual Core com Hyper Threading
  * 2GB de RAM DDR3
  * 160GB de HD + 160GB de HD secundario
  * GPU Integrada ao processador

#### Instalaçao do sistema

A instalaçao do sistema e feita da mesma forma que a versao Workstation do
Fedora, usando o instalador
[Anaconda](https://fedoraproject.org/wiki/Anaconda). A instalaçao demorou o
mesmo tempo que a instalaçao do Fedora Workstation ou qualquer spin do Fedora
(sim, ja usei todas elas). Ou seja, o processo foi demorado: processador fraco
+ HD lento, estou acostumado com minhas outras maquinas com SSD.

#### Problemas na instalaçao

Apos a instalaçao e apos fazer o setup inicial do GNOME, tive um problema com
o GDM, que ja havia sido reportado
[aqui](https://pagure.io/teamsilverblue/issue/76). Apesar de ter acesso ao TTY
para poder configurar a conexao com a internet pelo terminal, eu resolvi
instalar a versao 30, que ainda possui suporte, para prosseguir com meus
testes. Isso nao faria diferença porque o objetivo final era instalar o XFCE,
que esta na mesma versao no 30 e no 31.

#### Pos-instalaçao

Apos a instalaçao, fiz o rebase para a versao 31, mas obtive o mesmo erro
relatado acima, entao fiz o rollback para a versao 30 novamente (essa e uma
das vantagens de usar o Silverblue).

![](/img/1*kbR82k0LUVEHwaBBqWRWVQ.png)

Fedora Silverblue 30 instalado e funcionando

![](/img/1*9xuVcT5-85LYJOe2iit62A.png)

Usando o "Contas Online" para acessar meu Google Drive

Consumo do disco apos a instalaçao

![](/img/1*08XDQl6HdN3akvOnNwEVWA.png)

Consumo do disco com o sistema recem-instalado

Como eu esperava, o sistema nao ficou nada fluido com GNOME no meu Atom, entao
usei o projeto [Kinoite](https://discussion.fedoraproject.org/t/kinoite-a-kde-
and-now-xfce-version-of-fedora-silverblue/147) para instalar o ambiente
desktop XFCE.

Usei o excelente tutorial do Renato Araujo, do blog FastOS:
<https://fastoslinux.com/2019/07/30/silverblue-com-kde-plasma>

Se voces forem usar o Silverblue, visitem o blog FastOS, tem muita coisa sobre
o sistema.

#### Instalaçao do Ambiente XFCE

Fiz o rebase para o XFCE, e o download foi de 743MB

O sistema ficou muito mais leve com o Ambiente XFCE, mais leve, inclusive,do
que a spin XFCE do Fedora padrao .

![](/img/1*GKNLytW4KwkGAJtB4VDVnQ.png)

Consumo inicial de RAM e processador do Silverblue com XFCE

![](/img/1*iqYoYRbeKlA_K0izJMW8dw.png)

Apliquei o tema Greybird e troquei o wallpaper

Apos a instalaçao do XFCE o sistema passou a ocupar 11GB do HD, somando as
duas imagens: GNOME e XFCE, pois fiquei com os dois instalados e posso
escolher na hora do boot (GRUB).

#### Instalaçao de pacotes

Precisei instalar pacotes para usar o sistema (ora, mas que surpresa!). Optei
por usar dois metodos: rpm-ostree e Flatpak

Para alguns pacotes, principalmente de sistema e a GNOME Software, eu usei o
rpm-ostree, equivalente ao DNF no fedora padrao. E para outros pacotes, os de
programas desktop, preferi os flatpaks.

RPM Fusion Free

    
    
    rpm-ostree install https://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm

Apos o reboot (temos que fazer um reboot apos instalar pacotes com o rpm-
ostree, pois o sistema monta outro deploy do sistema todo a cada instalaçao)

    
    
    rpm-ostree install gnome-software xarchiver ffmpeg vim git neofetch gcc-c++ mesa-libGL-devel simplescreenrecorder

Obs.: instalei o gcc-c++ e o mesa-libGL-devel para rodar um programa em Qt que
estou fazendo num curso (usando o QtCreator). Insralei o simplescreenrecorder
para gravar os videos sobre o uso do sistema.

#### Vantagens do rpm-ostree

  * O rpm-ostree nao modifica ou substitui pacotes do sistema base, o que possibilita voltarmos para o sistema base em caso de necessidade
  * Se houver algum erro ou falta de conexao a internet durante a instalaçao, nenhuma alteraçao e feita e nao teremos pacotes quebrados pela interrupçao do instalador, basta refazermos a instalaçao com as devidas correçoes
  * O sistema armazena as camadas de pacotes instalados (layered packages), se o resultado da instalaçao nao for satisfatorio, podemos usar o rollback (que nao abordo aqui) e usar o sistema no estado em que ele estava antes

E existem mais vantagens, mas ainda sou um iniciante no sistema, farei mais
posts/videos ao longo do uso.

#### Desvantagem do rpm-ostree

A instalaçao de qualquer pacote com o rpm-ostree requer o reboot da maquina,
para podermos iniciar o novo deploy do sistema com os _layered packages_
instalados. Dica: fa ça uma lista de tudo que forem precisar para instalar
tudo de uma vez usando o rpm-ostree.

Fiz um video mostrando a instalaçao de pacotes com rpm-ostree:

#### Lidando com flatpaks

Para instalar alguns flatpaks, adicionei o repositorio flathub:

    
    
    flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo

Assim, pude usar a GNOME Software para instalar programas do repositorio
Flathub

![](/img/1*TVBQPRqq9KPe1WB-caWDvQ.png)

GNOME Software oferecendo a habilitaçao de repositorios de terceiros

![](/img/1*3urx0-ECTnfbm-o44t7r1g.png)

Flatpaks na GNOME Software

Pacotes instalados via flatpak:

  * Dbeaver: Cliente de bancos de dados
  * Geany: Editor de textos e IDE
  * Audacity: Editor de audio
  * KDEnlive: Editor de video
  * LibreOffice: A melhor suite de escritorio
  * Inkscape: Editor de desenhos vetoriais
  * GIMP: Editor de imagens

![](/img/1*EMLkBQ7onxlFp8QSISF26w.png)

LibreOffice Calc

Fiz um video sobre a instalaçao de Flatpaks no Fedora Silverblue:

#### Sobre o desempenho e uso de disco dos flatpaks

Pacotes flatpak requerem runtimes e SDKs para rodarem. Se todos os
empacotadores usassem o mesmo runtime para os pacotes que exigem GNOME, para
os que exigem KDE, etc., seria melhor. Mas receio que nunca havera uma
padronizaçao de runtimes e SDKs. Se quiserem ver como construir um flatpak,
fiz um tutorial, veja [aqui](https://medium.com/@leandroembu/construindo-seu-
primeiro-flatpak-47ae2d13d6b8).

Depois da introduçao acima, posso dizer que o consumo do disco da minha
maquina ficou um pouco acima do que seria consumido usando pacotes rpm
tradicionais, mas nao farei comparativos e nem graficos aqui. Se quiserem ver
um artigo sobre isso, vejam o post do FastOS
[aqui](https://fastoslinux.com/2019/11/23/fedora-rpm-vs-flatpak/).

Sobre o desempenho, nao notei nenhuma diferença entre os programas flatpak e
os rpm tradicionais na minha maquina, e eu ja fiz muitos videos sobre o Fedora
LXDE usando o mesmo computador, fora o fato de usar Fedora no mesmo PC ha
varios anos. Os programas rodam com o mesmo desempenho, tando com rpm quanto
com flatpak.

Consumo do disco antes de instalar o programa DBeaver:

![](/img/1*ieLl5DzPmaQMqBoUdI4icw.png)

Consumo do disco antes de instalar o dbeaver

Consumo do disco depois de instalar o DBeaver:

![](/img/1*qmBSNUbFyg8nmCRAtTCDiA.png)

Consumo do disco depois de instalar o dbeaver

Foram 2,3GB de disco para instalar o DBeaver. Claro que se outros programas
precisarem dos mesmos runtimes e SDKs que o DBeaver precisa, eles serao
compartilhados, e algumas partes dos runtimes tambem sao compartilhadas, as
vezes o flatpak baixa dependencias parciais e nao um runtime inteiro tambem.

Uso do disco antes e depois da instalaçao do editor/IDE Geany:

![](/img/1*sCZx9WFGDqqrr4lODDNJdQ.png)

Uso do disco antes da instalaçao do Geany

![](/img/1*unSkrubGe8WG1TAVSOjm0Q.png)

Uso do disco depois da instalaçao do Geany

No caso do Geany, o uso do disco foi de 1GB. Nao fiz o comparativo de todos os
outros programas.

#### Ajustes para maior fluidez do sistema

Para que o sistema rodasse melhor no meu PC, eu fiz algumas alteraçoes:

Eu nao criei partiçao de swap para o sistema, mas sim um arquivo de swap
depois do sistema instalado. Se quiser saber como criar um arquivo de swap,
leia o tutorial [aqui](https://medium.com/@leandroembu/criando-um-swapfile-no-
linux-838296fbcf3) ou veja o video que fiz abaixo:

Outros ajustes:

  * vm.swappiness=5
  * vm.vfs_cache_pressure=50

Se quiserem ver como fazer estes e outros ajustes, vejam o post do Fabio Akita
[aqui](https://www.akitaonrails.com/2017/01/17/optimizing-linux-for-slow-
computers) ou o video abaixo:

#### Sobre o uso do sistema

Eu fiquei surpreso ao usar o sistema no meu PC mais fraco. Esperava um sistema
mais lento por usar tantos conteineres, mas o que obtive foi um sistema leve e
gostoso de usar, comparavel ao Void Linux com XFCE que usei por tanto tempo no
mesmo computador. Para quem nao acompanhou, eu fiz muitos videos sobre o Void
com XFCE no mesmo computador
[aqui](https://www.youtube.com/playlist?list=PLIFOx3X8xDusLkOXjEtlSCfv17RNvQuwr).

Exceto as tarefas no navegador, que sao o [calcanhar de
Aquiles](https://www.significados.com.br/calcanhar-de-aquiles/) do meu PC, o
sistema esta rodando com uma fluidez surpreendente para o meu hardware, e esta
longe de usar todo o HD de 160GB que dediquei a ele.

Entendam: e um sistema moderno rodando com fluides num computador legado e que
ja era dos mais fracos na epoca em que foi lançado.

Existem algumas coisas que ainda nao conheço muito, vou tratar delas nos
proximos topicos.

#### O repositorio Flathub e confiavel?

O Fedora Silverblue foi concebido para ser usado com flatpaks. Existem alguns
repositorios nos quais tenho mais confiança: Fedora, GNOME e KDE Apps.

  * O repositorio de flatpaks do Fedora ainda tem poucos programas.
  * O repositorio kdeapps traz, nos apps que testei, programas _nightly_ , que sao versoes de teste para as proximas versoes estaveis.

O repositorio onde os programas flatpak funcionam melhor e o flathub. Eu sei
que muitos empacotadores que publicam no flathub sao os desenvolvedores dos
programas (upstream), mas o flathub nao mostra quem sao os mantenedores, todos
aparecem como Flathub Maintainers. Seria muito bom se o Flathub mostrasse, de
fato, quem mantem os pacotes.

![](/img/1*tiksm7DaxNO1iydaBBjwCQ.png)

GNOME Builder no repositorio Flathub

![](/img/1*H0YP3eJRL3NaqgAsRLwuVg.png)

Quem sao os mantenedores do GNOME Builder no Flathub?

#### Consideraçoes finais

O post poderia ser feito no forum da Comunidade Fedora Brasil, onde eu posto
muitas coisas. Mas preferi postar aqui por ter algumas opinioes pessoais.

Se alguem me perguntar se vale a pena usar o Fedora Silverblue, baseado na
minha experiencia no PC mais fraco que eu tenho, eu digo que sim, com
certeza.Se voces nao quiserem usar o kinoite (que vou falar sobre em outro
artigo), podem instalar outros ambientes desktop manualmente. Eu optei pelo
Kinoite porque ele nao apenas instala o ambiente XFCE, mas ja "faz a limpa" e
remove as coisas do GNOME instaladas anteriormente.

Como usei muitas coisas do flathub, eu gostaria de saber quem sao os
mantenedores dos pacotes, e nao apenas "Flathub Maintainers".

O Flathub sera o proximo "repositorio oficial" caso o Silverblue realmente
venha a substituir o Fedora Workstation? Ou vamos (sim, eu me incluo nisso)
levar os pacotes para o repositorio flatpak do Fedora? Sao perguntas sinceras,
e eu gostaria de ver o comentario de voces a respeito disso.

Nao tive problema nenhum em usar o Silverblue e os flatpaks num PC
extremamente fraco e velho, entao derrubei o mito que estava na minha propria
cabeça, sobre a fluidez do sistema: o argumento sobre o desempenho piorado por
usar flatpaks foi derrubado, e essa foi a maior motivaçao para eu ter começado
a empreitada de usar o Fedora Silverblue. No proximo ano vou instalar o
Silverblue no PC do meu trabalho (atualmente tenho o Debian Oldstable nele --
o Stretch) e usar ao longo do ano, tentando contribuir com o projeto e com a
comunidade.

P.S.: Se virem algum erro, me ajudem a corrigir.

E voces, conhecem o Silverblue? Tem algo a dizer sobre ele?

Um grande abraço e ate a proxima, pessoal.

