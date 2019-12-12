---
layout:	"post"
categories:	"blog"
title:	"Criando um swapfile no Linux"
date:	2018-09-16
thumbnail:	
author:	
---

* * *

Link para o video (na pratica): <https://youtu.be/mjq1_oq4SN8>

Muitas distribuiçoes Linux, entre elas o Ubuntu, estao usando arquivos de
troca (swap files) ao inves de uma partiçao dedicada a isso.

Muitas pessoas, dependendo do hardware e do uso da maquina, nao precisam
sequer usar swap -- e o meu caso em uma de minhas maquinas.

Nas maquinas em que uso swap, optei pelo arquivo de swap por algumas razoes:

  * Possibilidade de aumentar/reduzir o tamanho do swap
  * Possibilidade de deletar o arquivo de swap caso nao deseje mais usar
  * Possibilidade de transferir o arquivo de swap para outro disco ou partiçao, caso julgue necessario

Deixando o papo de lado, vamos aos passos para criar o swapfile.

* * *

#### 1- Meu cenario atual

    
    
    leandro@debian:~$ lsblk   
    NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT  
    sda      8:0    0 111,8G  0 disk   
    ├─sda1   8:1    0   524M  0 part /boot/efi  
    └─sda2   8:2    0 111,3G  0 part /  
    sdb      8:16   0 931,5G  0 disk   
    └─sdb1   8:17   0 931,5G  0 part /storage

No cenario acima, eu nao possuo partiçao de swap, e possuo um HD secundario de
1TB, que e onde vou colocar meu arquivo de troca. Voce pode colocar o seu em
qualquer lugar que desejar, nao precisa ter um disco extra para isso.

#### 2- Criando o arquivo de troca

Vou usar o fallocate, que aloca um espaço de disco para um arquivo:

    
    
    sudo fallocate -l 8G /storage/arquivo-de-troca

Se voce nao tiver o fallocate instalado:

    
    
    sudo dd if=/dev/zero of=/storage/arquivo-de-troca bs=1024 count=8388608

P.S.: O caminho do arquivo e o tamanho sao de sua escolha.

#### 3- Formatando o arquivo de troca

    
    
    sudo mkswap /storage/arquivo-de-troca

#### 4- "Ligando" o swap no arquivo criado

    
    
    sudo swapon /storage/arquivo-de-troca

#### 5- Verificando se o swap esta ativo no sistema

    
    
    sudo swapon --show

Com isso, voce devera ver seu arquivo de swap na saida do comando.

#### 6- Permitindo leitura e escrita somente para o root

Tenha a certeza de que somente o root podera ler e gravar o arquivo de troca

    
    
    sudo chmod 600 /storage/arquivo-de-troca

#### 7- Adicionando o arquivo de troca ao FSTAB

Para que o sistema inicie com o arquivo de swap montado e ativo, precisamos
colocar a entrada em nossa tabela de sistemas de arquivos (fstab ou
filesystems table). Edite o arquivo /etc/fstab em seu editor preferido, mas
com permissoes de root (ou sudo). Adicione a linha seguinte no final do
arquivo (lembre-se de colocar o caminho correto para o seu arquivo):

    
    
    /storage/arquivo-de-troca   none   swap  sw  0  0

#### 8- Reinicie o sistema

Para que suas mudanças tenham efeito, reinicie o sistema. Assim ele sera
iniciado montando o seu arquivo de swap e ativando o mesmo.

* * *

#### Conclusao

Criar um arquivo de swap nao e tao dificil, e ainda proporciona um bom
aprendizado sobre montagem de sistemas de arquivos que nao sao,
necessariamente, unidades de disco ou partiçoes -- Voce pode fazer isso para
criar um arquivo ext4, por exemplo.

Se tiver alguma duvida, por favor, comente. Eu nao mostrei como desabilitar e
excluir partiçoes de swap, caso voce tenha uma e queira trocar por swapfile,
mas talvez eu faça outro artigo ou ajude nos comentarios.

Obrigado pela leitura.

