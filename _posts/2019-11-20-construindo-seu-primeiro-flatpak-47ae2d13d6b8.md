---
layout:	"post"
categories:	"blog"
title:	"Construindo seu primeiro Flatpak"
date:	2019-11-20
thumbnail:	/img/0*FiwtrR8ZyDlYN7X4.jpg
author:	
---

* * *

![](/img/0*FiwtrR8ZyDlYN7X4.jpg)

Logo do Flatpak

Se quiserem me doar um cafe pelo PagSeguro do UOL: <https://pag.ae/7Vu8Tt-pn>

Depois de uma semana testando o Fedora Silverblue em duas maquinas, passei a
usar varios pacotes Flatpak, pois precisava conhecer melhor seu funcionamento.
Eu sou meio "das antigas" e prefiro usar os pacotes do repositorio da
distribuiçao Linux que estiver usando (no Fedora temos um repositorio de
flatpaks tambem, ainda pequeno). No entanto, nao posso negar que existem
vantagens no uso dos Flatpaks -- as quais nao vou abordar aqui para nao sair
do foco do artigo.

O tutorial a seguir e praticamente uma traduçao da documentaçao presente no
link <http://docs.flatpak.org/en/latest/first-build.html>

#### Ferramentas necessarias

Precisamos do **flatpak** e do **flatpak-builder**. No meu sistema (Fedora 31
Workstation), eles j a vem instalados. Veja como instalar no seu sistema --
provavelmente os dois pacotes estao nos repositorios da maioria das
distribuiçoes Linux, ou voce pode instalar o flatpak-builder como qualquer
flatpak

`flatpak install flathub org.flatpak.Builder`

#### Instalando o SDK necessario

Para construirmos nosso programa flatpak, vamos precisar do SDK apropriado
para isso. Aqui temos um ponto bastante discutido na comunidade, o tamanho dos
SDKs e Runtimes, mas isso sera debatido em outras midias (offtopic).

    
    
    flatpak install flathub org.freedesktop.Platform//18.08 org.freedesktop.Sdk//18.08

![](/img/1*krSGhfBclGz_iz6BdNwmZw.png)

Instalaçao do SDK necessario para fazermos o build do programa

#### Criando o programa

Sugiro que voce organize seus arquivos em algum diretorio, para que nao fiquem
misturados com outras coisas.

![](/img/1*1hlu_9eGC0_pF5tbMQHtvw.png)

Meu projeto em ~/projetos/flatpaks/org.leandroramos.Infoscript

Dentro do diretorio que escolhemos, vamos escrever o script, sera um script em
shell Bash para homenagear meu querido professor Blau Araujo, com quem faço um
curso -- <https://debxp-linux.blogspot.com/>

Vamos criar o arquivo infoscript.sh e colocar o seguinte conteudo:

    
    
    #!/usr/bin/env bash  
    clear  
    echo ""  
    echo "Informaçoes super importantes!"  
    echo " -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -"  
    echo -n "Usuario : "  
    whoami  
    echo -n "Hostname: "  
    hostname  
    echo -n "Uptime : "  
    uptime -p  
    echo -n "Kernel : "  
    uname -rms  
    echo " -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -- -"  
    echo ""

![](/img/1*cvlTnUr5a7a-Nojdxfzjrg.png)

Script no editor de textos

#### Criando o "manifesto"

Todo pacote flatpak e construido usando um arquivo manifest que possui
informaçoes basicas sobre o programa e instruçoes para que ele seja construido
(ou, no novo verbo, "buildado"). Vamos criar o arquivo
org.leandroramos.Infoscript.json (OK, nao precisam usar o meu nome aqui) no
mesmo diretorio onde colocamos o infoscript.sh, e adicionar o seguinte
conteudo (adapte para o seu uso ai):

    
    
    {  
        "app-id": "org.leandroramos.Infoscript",  
        "runtime": "org.freedesktop.Platform",  
        "runtime-version": "18.08",  
        "sdk": "org.freedesktop.Sdk",  
        "command": " **infoscript.sh** ",  
        "modules": [  
            {  
                "name": " **infoscript** ",  
                "buildsystem": "simple",  
                "build-commands": [  
                    "install -D infoscript.sh /app/bin/ **infoscript.sh** "  
                ],  
                "sources": [  
                    {  
                        "type": "file",  
                        "path": " **infoscript.sh** "  
                    }  
                ]  
            }  
        ]  
    }

![](/img/1*Kr9fBl5A_uS__-UNRFd1yg.png)

Manifesto json no editor de textos

#### Construindo o programa (build)

Agora que o nosso programa tem um manifesto, o flatpak-builder pode construir
o pacote. Ao especificar o build-dir (que pode ter outro nome), teremos um
diretorio com o build do programa.

    
    
    flatpak-builder build-dir org.leandroramos.Infoscript.json

![](/img/1*8_9AiAliZOwd5WHsS2l15w.png)

Build concluido

![](/img/1*QR15AmnKKOmIJM2uUSbG2w.png)

Conteudo do build-dir

#### Testando o build do programa

Me perdoem por misturar as palavras construçao e build, mas acho que nao devo
mais traduzir assim.

Para testar o programa, vamos usar o flatpak-builder. Usando o parametro run,
o programa tera quase as mesmas permissoes de um programa final, exceto as
permissoes de acesso ao sistema de arquivos.

    
    
    flatpak-builder --run build-dir org.leandroramos.Infoscript.json infoscript.sh

![](/img/1*2l6J_HYZ7IYF6aMh5QNSyg.png)

Primeiro programa Flatpak funcionando

#### Colocando o pacote num repositorio

Antes de podermos instalar e rodar o programa, ele precisa estar em um
repositorio. Vamos criar um repositorio local para o nosso primeiro programa,
e devo lembrar que voce pode colocar o nome que quiser no repositorio, pois
estamos trabalhando localmente.

    
    
    flatpak-builder --repo=leandroramos --force-clean build-dir org.leandroramos.Infoscript.json

O comando acima vai fazer o build novamente e exportar o resultado para um
diretorio chamado _leandroramos_  -- que e o meu repositorio local. O segundo
parametro (force-clean) vai esvaziar o diretorio build-dir criado
anteriormente.

![](/img/1*cdqjpkPcqPpkcz9wBM3sPQ.png)

Colocando o programa no repositorio

![](/img/1*nDIB0_1Z8wyxNzbgidjboQ.png)

Conteudo do repositorio leandroramos

#### Instalando o programa

Antes de instalarmos o programa, como todo flatpak, precisamos adicionar o
repositorio a nossa lista de remotos (voce pode consultar a pagina [Using
Flatpak](http://docs.flatpak.org/en/latest/using-flatpak.html) para entender
melhor).

    
    
    flatpak --user remote-add --no-gpg-verify leandroramos leandroramos

Depois podemos listar os remotos para conferir se o novo repositorio foi
adicionado

    
    
    flatpak remotes

E, depois, podemos instalar o programa

    
    
    flatpak --user install leandroramos org.leandroramos.Infoscript

![](/img/1*OUGIEh8rhHMezvrGEIkZ1A.png)

Instalando o programa Infoscript a partir do repositorio leandroramos

Note que passamos o parametro `--no-gpg-verify`quando adicionamos o
repositorio _leandroramos_ a lista de remotos do flatpak. Faça isso somente em
testes locais. Para publicar programas em repositorios oficiais voce deve
assinar os pacotes com chave privada GPG.

#### Finalmente, rodando o programa

O nosso programa nao possui lançadores nem integraçao alguma com o sistema, e
nem precisaria no momento. Entao, vamos executa-lo a partir do terminal (a
partir de qualquer lugar do sistema, nao precisamos mais estar no diretorio de
criaçao do pacote).

    
    
    flatpak run org.leandroramos.Infoscript

![](/img/1*LcRBNo9E5jaDJbtmDNtVDQ.png)

Comando para rodar o programa Infoscript

![](/img/1*nXAvjtpi1LQxBsCqoHJCPA.png)

Execuçao do programa Infoscript

Por enquanto e so, pessoal. Abraços!

