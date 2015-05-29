---
layout: page
title: "Funções"
description: ""
---
{% include JB/setup %}

{% include menu/functions.md %}

## Motivação {#motivacao}

* Legibilidade
* Mantenabilidade
* Separação de Código
* Modularidade
* Nosso professor de Ciência da Computação disse para fazer assim
* Se fizéssemos diferente disso zombariam de nós

* * *


## Características {#caracteristicas}

{% highlight php5 linenos %}
<?php
function nomeDaFuncao() { }
{% endhighlight %}

* Todas as funções no PHP retornam um valor (nulo caso a cláusula `return` não for usada).
* Os nomes das funções não fazem distinção entre maiúsculas e minúsculas
* global $id; // GLOBALS['id'];
* O PHP 5 permite que sejam definidos valores padrões para os parâmetros mesmo quando eles forem declarados por referência (se uma variável não é passada, uma nova é criada)
* No PHP4 os objetos eram passados por valor (ByVal).
* No PHP5 os objetos são sempre passados por referência (ByRef), a menos que, de forma explícita, se faça um clone dele.
* Seria "_" válido como nome de uma função?

{% highlight php5 linenos %}
<?php
function printList($string, $count = 5)

function newTo5(&$number = 2)

$a = func_get_args();

int func_num_args(void)

mixed func_get_arg ( int $arg_num )
{% endhighlight %}

* * *

## Retorno por referência {#retorno_por_referencia}

[http://php.net/manual/pt_BR/language.references.return.php](http://php.net/manual/pt_BR/language.references.return.php)

{% highlight php5 linenos %}
<?php
function &nomeDaFuncao() { }
{% endhighlight %}

* permite que, em vez de uma cópia, seja retornada uma variável como resultado da função
* é usado para coisas como recursos e na implementação do padrão Factory
* você é obrigado a retornar uma variável
* você não pode retornar uma expressão por referência
* você não pode retornar uma declaração `return` vazia para forçar o retorno de um valor NULL

* * *

## Funções Anônimas, closures {#funcoes_anonimas_closures}

[http://php.net/manual/pt_BR/functions.anonymous.php](http://php.net/manual/pt_BR/functions.anonymous.php)

Permitem a criação de funções sem nome específico. Elas são úteis principalmente como valores de parâmetros [callback](http://www.php.net/manual/pt_BR/language.pseudo-types.php#language.types.callback), mas elas tem muitos outros usos.

As closures também podem ser usadas como valores de variáveis; o PHP converte automaticamente essas expressões em instâncias da classe interna `Closure`.

{% highlight php5 linenos %}
<?php
$cumprimentar = function($nome)
{
    printf("Olá %s\r\n", $nome);
};

$cumprimentar('Mundo');
$cumprimentar('PHP');
?>
{% endhighlight %}

É possível usar as funções [func_num_args()](http://www.php.net/manual/pt_BR/function.func-num-args.php),  [func_get_arg()](http://www.php.net/manual/pt_BR/function.func-get-arg.php) e [func_get_args()](http://www.php.net/manual/pt_BR/function.func-get-args.php) de dentro de uma closure.

A classe final predefinida `Closure` foi introduzida no PHP 5.3.0. Ela é usada para a implementação interna das [funções anônimas](http://www.php.net/manual/pt_BR/functions.anonymous.php).
A classe tem um construtor que proíbe a criação manual do objeto (disparando um `E_RECOVERABLE_ERROR`) e o método `__invoke` via chamada mágica.

Também podem herdar variáveis do escopo pai.

{% highlight php5 linenos %}
<?php
$callback =
            function ($quantidade, $produto) use ($imposto, &$total)
            {
                $precoPorItem = constant(__CLASS__ . "::PRECO_" .
                    strtoupper($produto));
                $total += ($precoPorItem * $quantidade) * ($imposto + 1.0);
            };

        array_walk($this->produtos, $callback);
{% endhighlight %}
