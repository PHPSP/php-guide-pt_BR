---
layout: page
title: "Programação Orientada a Objetos"
description: ""
---
{% include JB/setup %}

{% include menu/oop.md %}


* * *

## Fatos

* Antes do PHP 5, POO (Programação Orientada a Objetos) era um hack implementado com arrays
* Mais lento que código procedural, mas permite que tarefas complexas sejam entendidas de forma legível
* Objetos agora são tratados por referência em vez de por valor, objetos devem ser explicitamente clonados para que sejam copiados


* * *

## PPP & F


* Public – Método ou propriedade pode ser acessado de fora
* Private – Método ou propriedade é privada à classe e não pode ser acessada de fora
* Protected – Método ou propriedade é privado, mas pode ser acessado por classes herdeiras
* Final – Método não pode ser sobrescrito por classes herdeiras


* * *

## Constantes, Membros Estáticos


* são acessíveis como parte da própria classe
* chamar propriedades estáticas usando a notação de objeto resultará em um notice
* por padrão, métodos ou propriedades estáticos são considerados públicos
* constantes de classes são públicas e acessíveis de todos os escopos
* constantes podem somente conter valores escalares
* código muito mais limpo
* significantemente mais rápidas do que aquelas declaradas com define()


* * *

## Interfaces e Classes Abstratas


* Nova funcionalidade adicionada ao PHP 5
* Utilizadas para criar uma série de restrições no design básico de um grupo de classes
* Você deve declarar uma classe como abstrata quando esta tiver (ou herdar sem implementar) ao menos um método abstrato
* Uma classe pode herdar somente uma outra classe, mas pode implementar multiplas interfaces


* * *

## Instanceof

Permite inspecionar todas as classes de seu objeto, assim como quaisquer interfaces


* * *

## Carregamento automático

{% highlight php5 linenos %}
<?php
function __autoload($class_name)
{
    require_once "/www/phpClasses/{$class_name}.inc.php";
}
$a = new friend;
{% endhighlight %}


* * *

## Funções Especiais


* <http://php.net/manual/pt_BR/language.oop5.magic.php>
* `__construct()`
* `__destruct()` - Uma destruição ocorre quando não existem mais referências ao objeto, e isto pode não ocorrer quando você espera ou gostaria que ocorresse.
* `__toString()`
* `__sleep()`
* `__wakeup()`
* `__call()`
* `__get()`
* `__set()`


* * *

## Exceções


* Método unificado de tratamento de erros
* Torna possível o tratamento adequado de erros
* Pode ser realizado com blocos try catch ou definindo um único tratador de erros uma vez
* Blocos try catch tomam precedência se o código que gera o erro está dentro destes
* São objetos, criados (ou "lançados") quando um erro ocorre
* Todas as exceções não tratadas são fatais
* A porção `catch()` requer que digamos o tipo da exceção
* `callback set_exception_handler ( callback $exception_handler )`
* `bool restore_exception_handler ( void )`


* * *

## SPL


* permite empilhar um autoloader em cima de outro
* `void spl_autoload ( string $class_name [, string $file_extensions = spl_autoload_extensions() ] )`
* `string spl_autoload_extensions ([ string $file_extensions ] )`
* `bool spl_autoload_register ([ callback $autoload_function [, bool $throw = true [, bool $prepend = false ]]] )` - first call to this function replaces the __autoload() call in the engine with its own implementation


* * *

## API Reflection


* <http://php.net/reflection>
* provê uma forma de obter informação detalhada sobre um código
* `$func = new ReflectionFunction($func);`
* `ReflectionClass`
* `ReflectionMethod`
* `array get_defined_functions ( void )`
* `array get_object_vars ( object $object )`


* * *

## Indução de Tipo

<http://php.net/manual/pt_BR/language.oop5.typehinting.php>


* * *

## Late Static Binding

<http://php.net/manual/pt_BR/language.oop5.late-static-bindings.php>
