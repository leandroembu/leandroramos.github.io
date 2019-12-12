---
layout:	"post"
categories:	"blog"
title:	"Software Livre, Software Proprietário e os anseios da comunidade ao longo dos anos"
date:	2019-12-11
thumbnail:	/img/0*fR59pMEKgqEjAf6V.jpg
author:	
---

* * *

![](/img/0*fR59pMEKgqEjAf6V.jpg)

Primeiro lançamento do Ubuntu -- 4.10 Warty Warthog

Hoje vou falar um pouco sobre _software_ livre, _software_ propriet ario e
sobre a mudança nos anseios da comunidade Linux ao longo dos anos. Nao estarei
dizendo que as pessoas que usam Linux nao devem usar _software_ propriet ario,
eu mesmo preciso usar alguns, por falta de escolha. E falta de escolha tambem
faz parte do texto a seguir.

#### Motivaçao

Durante os ultimos dias eu procurei por algum adaptador _wireless_ USB para
meus computadores, e depois de uma conversa com alguns colegas, resolvi
procurar por algum que n ao dependesse de _firmware_ propriet ario para
funcionar.

Durante minha busca, notei que os _hardwares_ que eu estava procurando eram
mais comuns h a alguns anos, especialmente na decada passada, e hoje temos que
procurar muito. Eu so encontrei em algumas lojas internacionais.

Isso me fez pensar sobre como esta mais dificil encontrar tais _hardwares_
hoje em dia, e isso me motivou a falar sobre o assunto.

#### Um pouco de historia

Houve uma epoca, do inicio dos anos 2000 ate 2010, mais ou menos, em que
tivemos um movimento forte pelo _software_ livre (ainda bem que em portugu es
temos uma palavra que nao significa o mesmo que "gratis").

Nessa epoca, tinhamos mais _hardwares_ que funcionavam com _software_ livre,
inclusive os adaptadores _wireless_ e processadores que n ao precisavam do
_microcode_ propriet ario. Basta fazer uma busca por ano aqui --
[https://h-node.org](https://t.co/etEoQvtxaQ?amp=1 "https://h-node.org/") -- e
ver quando tinhamos mais opçoes.

Vejam uma busca por adaptadores _wireless_ que funcionam em sistemas livres,
buscando pelo ano de 2010, apareceram oito dispositivos USB e dois
dispositivos PCI:

![](/img/1*pjHXQZOOXnjvuGABrVUjRg.png)

Busca por adaptador wireless "livre" em 2010

Agora vejam a mesma busca, so que em 2018. Nao aparece nenhum dispositivo:

![](/img/1*umrJNdJKbgobnOj8HirEDQ.png)

Busca por adaptador wireless "livre" em 2018

Nao acompanhei a decada de 1990 no _software_ livre. N ao por falta de idade,
mas por nao imaginar o que era Linux na epoca. Mas eu usava bastante
_freeware_ , que na epoca tambem ajudaram a confundir as pessoas, pois
misturavam _freeware_ com software livre, especialmente porque em ingl es a
palavra _free_ serve tanto para  "livre" quanto para "gratis".

Os _freewares_ s ao softwares gratuitos, mas nao sao livres, nao
disponibilizam codigo-fonte, nao permitem que voce redistribua (inclusive
fazendo modificaçoes para redistribuir), limitam a quantidade de maquinas em
que voce pode instalar, etc. Nao vou me aprofundar nos conceitos de software
livre, _software_ _opensource_ e _freeware_ no momento.

Os _freewares_ ainda existem, e ainda confundem os usu arios (mesmo tendo as
palavras "livre" e "gratis" disponiveis no nosso idioma), e para usa-los voce
precisa concordar com suas licenças, que muitas vezes aparecem como EULA
(voces ja viram isso, eu sei). Alguns exemplos de _freewares_ atuais s ao WPS
Office Community, FreeOffice, Visual Studio Code*, Google Chrome, etc.

*Se quiserem entender sobre a diferença das licenças entre o Visual Studio Code e o Code OSS (base do VSCode), vejam [aqui](https://code.visualstudio.com/docs/supporting/faq).

Apos o desvio para falar sobre os _freewares_ , vou retomar o fio da meada.

#### Do inicio da decada de 2010 ate hoje (2019)

Recapitulando o que eu disse no topico anterior, sobre as decadas passadas:

> Nessa epoca, tinhamos mais hardwares que funcionavam com software livre

Hoje temos um movimento contrario: temos cada vez mais _hardwares_ que n ao
funcionam sem _firmwares_ propriet arios. E o que me assusta e que **n ao
reclamamos por isso**. Ao inves disso, clamamos para que mais _softwares_
propriet arios venham para o Linux para que possamos usar esses _hardwares_.

Entendam: nao ha problemas em usar _software_ propriet ario para que seus
_hardwares_ funcionem plenamente, afinal, voc es pagaram pelo hardware e
merecem usa-lo com todos os recursos disponiveis. Entendam esse ponto, e muito
importante.

O problema e a **mudan ça de direçao** das coisas: nas decadas passadas, a
comunidade Linux pedia por mais _hardware_ que funcionasse com _software_
livre. Hoje em dia **a comunidade clama por mais softwares propriet arios**
para seus _hardwares_ funcionarem, e eu n ao vejo (se tiver, eu ainda nao vi)
um movimento reclamando pela abertura de _firmwares_ , tornando-os livres, ou
pela nao necessidade de _firmware_ algum para que um simples adaptador
_wireless_ funcione sem nada propriet ario. Um exemplo de _hardware_ que
depende do _firmware_ propriet ario e a minha placa _wireless  _-- Intel 7265,
ela nao funciona sem _firmware_ propriet ario, e muita gente acha que e livre
porque funciona "de primeira" na maioria das distribuiçoes Linux -- mas essas
distribuiçoes trazem o _firmware nonfree_ no seu instalador, para que o usu
ario nao fique sem internet, e isso e bom (enquanto nao temos uma soluçao
realmente livre).

![](/img/1*Fxed3-3_Qp3X6Cmw-WWNmw.png)

Minha Wireless Intel 7265

Percebem a diferença de direçao? Antes, queriamos mais _hardware_ independente
de _software_ propriet ario, hoje queremos mais _software_ propriet ario para
o nosso _hardware._ Implic ancia minha? Podem dizer que sim, mas e uma mudança
de direçao.

Uma boa iniciativa para contornar a necessidade de _drivers_ e _firmwares_
propriet arios e o Projeto [_Nouveau_](https://nouveau.freedesktop.org/wiki/),
que tem o objetivo de prover _drivers_ livres para placas de v ideo nVidia,
inclusive portando o software para o NetBSD. Esta longe de ser o ideal, mas
pensem duas vezes antes de falarem mal do projeto e, se possivel, ajudem.

#### Exemplificando melhor a mudança nos anseios da comunidade

Saindo um pouco dos _firmwares_ , vou falar sobre outra coisa que mostra, mais
claramente, a mudança de direçao:

Voces ja perceberam ou viram algum movimento que cobre do Microsoft Office uma
maior compatibilidade com os formatos abertos, ou que ele pare de mudar o
layout de documentos feitos em outros programas? Aposto que nao. Justamente
pelo MS Office ser proprietario e fechado e dificil pedir alguma coisa (issue
no repositorio dele? hehe). E infelizmente e a suite de escritorio mais usada,
especialmente no meio corporativo.

Nao, nos nao pedimos para ele ser mais compativel, e o pior: nao ajudamos os
softwares livres a melhorarem, e eu me incluo nisso. E pior ainda: pedimos
para que o Microsoft Office venha para o Linux, para que o mundo todo seja
compativel com ele -- essa e a mudança de direçao a que me refiro aqui,
favorecer o software proprietario em vez de favorecer a **liberdade do usu
ario** (tema de um futuro post).

#### De onde vem a mudança de direçao?

Essa mudança de direçao, ou mudança nos anseios da comunidade Linux, pode ter
vindo de varios lugares, entao e uma questao que deixo aqui para voces. Mas
vou mostrar uma delas, vejam o anuncio do primeiro lançamento do Ubuntu, o
4.10 Warty Warthog [aqui](https://lists.ubuntu.com/archives/ubuntu-
announce/2004-October/000003.html).

![](/img/1*mGdHhOEF74wWoWrJgKWnHw.png)

Anuncio do Ubuntu 4.10, primeiro lançamento do Ubuntu

Destaquei um trecho da imagem acima:

> Absolutamente comprometido com software livre, todo programa para o usuario
final, no CD, e software livre.

E quem acompanha a historia do Ubuntu sabe que isso mudou (e muito) na decada
atual. Claro que tem justificativa: trazendo software proprietario no seu (CD)
arquivo ISO, ele garante que o sistema vai funcionar para o maior numero de
usuarios possivel, e isso contribui para que o sistema se popularize. No
entanto, deixo outras questoes para voces:

A Canonical nao tem algum poder, mesmo que pouco, de convencer pelo menos um
fabricante de hardware a abrir seus drivers e firmwares? Estou citando apenas
a Canonical, mas juntemos as maiores empresas que lidam com Linux, elas nao
tem alguma força para isso? Ou nao querem? Ou fazem e eu nao vi? (Pode ser que
eu nao tenha visto, abram meus olhos, por favor, e dormirei melhor).

#### A comunidade pode fazer alguma coisa sobre isso?

Acredito que a comunidade nao possa fazer muita coisa. Mas uma coisa ela nao
pode deixar de ser: **questionadora**. Temos que questionar essas coisas, por
que temos gigantes da tecnologia usando e fazendo software livre e estamos
cada vez mais entupidos de software propriet ario -- e clamando por mais
softwares proprietarios?

Quem nao viveu ou nao prestou atençao nas decadas passadas nao entende o
inconformismo de quem esta vendo essa transiçao da luta por coisas que
respeitam a liberdade do usuario para o

> tanto faz, desde que funcione

Entao, quando virem alguem falar sobre _software_ livre e liberdade do usu
ario, nao atirem pedras, vamos conversar, pois sua liberdade e tirada de voces
todos os dias, ate nas embalagens dos produtos que escondem informaçoes
importantes, e voces acabam comprando produtos sem saberem o _chipset_ , as
vezes nem a versao (ou lote) do modelo do equipamento. Alguem de voces ja
conseguiu testar um adaptador _wireless_ ou outros dispositivos antes da
compra? Isso tem a ver com nossas liberdades.

O "tanto faz" e perigoso demais. Se formos por esse caminho, logo teremos um
kernel livre rodando um monte de coisas que nao sabemos de onde vem, como sao
feitas e nem o que fazem com nossos dados.

Muito obrigado pela leitura. Ate a proxima, pessoal!

