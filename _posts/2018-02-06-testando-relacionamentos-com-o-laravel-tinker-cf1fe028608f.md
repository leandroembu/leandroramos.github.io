---
layout:	"post"
categories:	"blog"
title:	"Testando relacionamentos com o Laravel Tinker"
date:	2018-02-06
thumbnail:	/img/1*my5GxEYdzcv2PHtiPPosSg.png
author:	
---

* * *

![](/img/1*my5GxEYdzcv2PHtiPPosSg.png)

Shell interativo do Laravel

Se quiserem me doar um cafe pelo PagSeguro do UOL: <https://pag.ae/7Vu8Tt-pn>

O Tinker e um console interativo do Laravel, um shell do PHP com acesso as
classes do nosso projeto. Uma das coisas que mais gosto de fazer no Tinker e
testar meus relacionamentos e queries no banco de dados. Para fazer uma
pequena demonstraçao, e bom começarmos pelo começo, desde a criaçao do
projeto.

Nosso super projeto de controle de vendas tera duas tabelas no banco de dados,
com um relacionamento 1:n

![](/img/1*mbjMDKylYYQcyQvwvXhKzg.png)

Poucos campos. O suficiente para brincarmos com o Tinker.

Primeiro, crie um banco de dados (no SGBD de sua preferencia), depois crie o
projeto:

    
    
    composer create-project laravel/laravel sales --prefer-dist

Crie os models necessarios (a opçao -mf e para que tambem sejam gerados
migration e factory para os models):

    
    
    php artisan make:model Seller -mf  
    php artisan make:model Sale -mf

Abra a migration database/migrations/***create_sellers_table.php (***
significa um monte de numeros que indicam a hora em que a migration foi
criada). Deixe o metodo up com o seguinte codigo:

    
    
    public function up()  
    {  
        Schema::create('sellers', function (Blueprint $table) {  
            $table->increments('id');  
            $table->string('name');  
            $table->string('email');  
            $table->timestamps();  
        });  
    }

Faça o mesmo com a migration database/migrations/***create_sales_table.php:

    
    
    public function up()  
    {  
        Schema::create('sales', function (Blueprint $table) {  
            $table->increments('id');  
            $table->integer('price');  
            $table->integer('seller_id')->unsigned();  
            $table->timestamps();
    
    
            /** Abaixo vai a chave estrangeira  
              * do nosso relacionamento  
              */
    
    
            $table->foreign('seller_id')  
                  ->references('id')  
                  ->on('sellers');  
            });  
        }

Agora voce pode migrar o banco de dados:

    
    
    php artisan migrate

Agora faça alguns ajustes nos models, para configurar o nosso relacionamento
um-para-muitos:

Deixe o arquivo app/Sale.php com o seguinte codigo:

    
    
    <?php
    
    
    namespace App;
    
    
    use Illuminate\Database\Eloquent\Model;
    
    
    class Sale extends Model  
    {  
        public function seller()  
        {  
            return $this->belongsTo('App\Seller');  
        }  
    }
    
    
    /* o belongsTo usado acima informa que cada venda (sale) pertence a um vendedor (seller) */

Deixe o arquivo app/Seller.php com o seguinte codigo:

    
    
    <?php
    
    
    namespace App;
    
    
    use Illuminate\Database\Eloquent\Model;
    
    
    class Seller extends Model  
    {  
        public function sales()  
        {  
            return $this->hasMany('App\Sale');  
        }  
    }  
    /* O hasMany acima informa que nosso vendedor (seller) pode possuir uma ou mais vendas (sales) */

As classes acima, basicamente, dizem que uma Sale (venda) pertence a um Seller
(vendedor), atraves do metodo seller() - e um Seller (vendedor) pode possuir
varias Sales (vendas), atraves do metodo sales().

Agora ja podemos usar o Tinker para algumas operaçoes com nossas classes,
digite no terminal:

    
    
    php artisan tinker

Com o tinker aberto, vamos criar um vendedor:

    
    
    >>> $seller = new Seller  
    >>> $seller->name = "John Doe"  
    >>> $seller->email = "john.doe@foo.bar"  
    >>> $seller->save()

Verifique se os dados estao gravados no banco de dados:

    
    
    >>> Seller::all()  
    => Illuminate\Database\Eloquent\Collection {#748  
         all: [  
           App\Seller {#749  
             id: 1,  
             name: "John Doe",  
             email: "john.doe@foo.bar",  
             created_at: "2018-02-06 17:48:08",  
             updated_at: "2018-02-06 17:48:08",  
           },  
         ],  
       }  
    >>>

Com nosso vendedor gravado, sabemos que seu ID e 1 (no meu caso, no seu pode
ser outro ID). Vamos cadastrar duas vendas para o nosso vendedor:

    
    
    >>> $sale1 = new Sale  
    >>> $sale2 = new Sale  
    >>>   
    >>> $sale1->price = 13699  
    >>> $sale1->seller_id = 1  
    >>> $sale2->price = 30000  
    >>> $sale2->seller_id = 1  
    >>>  
    >>> $sale1->save()  
    >>> $sale2->save()

Agora que temos nosso vendedor gravado, com suas duas vendas, voce pode fazer
algumas consultas interessantes, faça algumas consultas e diga o que achou do
Tinker.

    
    
    /* todas as vendas do vendedor */
    
    
    >>> $seller->sales  
    => Illuminate\Database\Eloquent\Collection {#737  
         all: [  
           App\Sale {#747  
             id: 1,  
             price: 16499,  
             seller_id: 1,  
             created_at: "2018-02-06 17:58:35",  
             updated_at: "2018-02-06 17:58:35",  
           },  
           App\Sale {#745  
             id: 2,  
             price: 30000,  
             seller_id: 1,  
             created_at: "2018-02-06 17:58:39",  
             updated_at: "2018-02-06 17:58:39",  
           },  
         ],  
       }
    
    
    /* Dados da segunda venda */  
    >>> $sale = Sale::find(2)  
    => App\Sale {#753  
         id: 2,  
         price: 30000,  
         seller_id: 1,  
         created_at: "2018-02-06 17:58:39",  
         updated_at: "2018-02-06 17:58:39",  
       }
    
    
    /* Para saber quem foi o vendedor da segunda venda */  
    >>> $sale->seller->name  
    => "John Doe"

As operaçoes acima sao muito simples, claro. Mas o relacionamento nos poupa de
importar muitas classes, e podemos usar coisas com HasManyThrough, que
tornariam o artigo muito longo e cansativo.

Eu outro artigo, vou mostrar como usar as factories para popularmos nosso
banco de dados de forma mais rapida.

Se quiser ver o codigo, testar, brincar, etc., siga o link para o branch
"part1" no meu repositorio sales:
<https://github.com/leandroramos/sales/tree/part1>

Experimente o Laravel Tinker, e se quiser deixe sua opiniao nos comentarios.
Obrigado pela leitura.

Para saber mais:

[ **Eloquent: Relationships**  
 _Database tables are often related to one another. For example, a blog post
may have many comments, or an order could be
…_laravel.com](https://laravel.com/docs/5.4/eloquent-relationships
"https://laravel.com/docs/5.4/eloquent-
relationships")[](https://laravel.com/docs/5.4/eloquent-relationships)

