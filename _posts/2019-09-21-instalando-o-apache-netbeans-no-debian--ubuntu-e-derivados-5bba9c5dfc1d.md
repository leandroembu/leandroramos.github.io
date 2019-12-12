---
layout:	"post"
categories:	"blog"
title:	"Instalando o Apache Netbeans no Debian, Ubuntu e derivados"
date:	2019-09-21
thumbnail:	/img/1*v8aTArhV_nYQRQtcQa5VkQ.png
author:	
---

* * *

Instalar o Apache Netbeans no Debian, Ubuntu e derivados e simples, mas ainda
deixa muitos usuarios em duvida. Vou mostrar como fazer isso em passos
simples.

Para que isso funcione em qualquer distro baseada no Debian e em qualquer
ambiente desktop, vou mostrar como fazer as coisas pelo terminal, mas voce
pode usar ferramentas como Synaptic, Muon ou MintInstall, por exemplo.

#### Instalando as dependencias

    
    
    sudo apt install openjdk-11-jdk

#### Faça o download do Apache Netbeans em sua ultima versao

Acesse a pagina de downloads em
<https://netbeans.apache.org/download/index.html>

Clique no botao de download da ultima versao (quando escrevi o artigo era a
versao 11.1)

![](/img/1*v8aTArhV_nYQRQtcQa5VkQ.png)

Pagina de downloads do Apache Netbeans

Baixe o arquivo para Linux (o que tem a extensao .sh), na data do artigo era o
link <https://www.apache.org/dyn/closer.cgi/netbeans/netbeans/11.1/Apache-
NetBeans-11.1-bin-linux-x64.sh>

#### Dando permissao de execuçao ao instalador

Voce pode fazer isso clicando com o botao direito do mouse no arquivo baixado
-> Propriedades -> Permissoes -> Permitir execuçao como programa.

Ou, no terminal, na pasta onde esta o arquivo:

    
    
    chmod +x Apache-NetBeans-11.1-bin-linux-x64.sh

#### Instalando o Netbeans

Pelo gerenciador de arquivos, voce pode simplesmente dar um clique duplo no
arquivo e a instalaçao vai começar.

Pelo terminal, na pasta onde esta o arquivo baixado:

    
    
    ./Apache-NetBeans-11.1-bin-linux-x64.sh

Obs.: Nao se esqueça do ponto-barra ./ antes do nome do arquivo. Vou falar
sobre isso no meu curso de terminal para iniciantes, no meu [canal no
YouTube](https://www.youtube.com/playlist?list=PLIFOx3X8xDuuoDoE7hHglfooiQ70Xi1ot)

![](/img/1*0MfFwS6_5hJXRrvPPrJZVQ.png)

Comando para executar o instalador

![](/img/1*OoTqGTH6ZrBHM_a5To49IA.png)

Primeira tela do instalador

![](/img/1*gThYtBH1nsn1xQZZC7HgJQ.png)

Aceitando os termos da licença

![](/img/1*QiPWwmBq-Oz1gKNfuTaIBg.png)

Selecionando a pasta de instalaçao e o ambiente Java

![](/img/1*uJgvL4gWJknNIbfo-IKPMQ.png)

Iniciando a instalaçao do Apache Netbeans

![](/img/1*GcwbwptgUxOQdYQw191yhg.png)

Agora basta aguardar o fim da instalaçao

Apos a instalaçao, o Apache Netbeans estara no menu do seu sistema.

#### Desinstalando o Apache Netbeans

Abra o terminal na pasta onde esta a instalaçao Apache Netbeans

![](/img/1*ljYo0ZmU3NOCxQHwGxLa1g.png)

Abrindo o terminal na pasta do Netbeans

Ou, pelo terminal:

    
    
    cd ~/netbeans-11.1

Depois execute o desinstalador:

    
    
    ./uninstall.sh

![](/img/1*Ns57aTAN2oLKj7oGvQAogw.png)

Comando para desinstalar o programa

![](/img/1*DvRwZaL8vn0jjNRxT5fBZQ.png)

Confirmar a desinstalaçao

![](/img/1*j795OXLL_COHB5q6L0XRaA.png)

Aguarde o fim do processo de desinstalaçao

Obrigado pela leitura, ate a proxima, pessoal!

