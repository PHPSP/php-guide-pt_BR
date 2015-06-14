---
layout: page
title: "Design e Teoria"
description: ""
---
{% include JB/setup %}

{% include menu/design-and-theory.md %}


* * *

## Para ver


* [SPL](http://php.net/spl) (standard PHP Library)
* [PECL](http://pecl.php.net/) (PHP Extension Community Library)
* [PEAR](http://pear.php.net/) (PHP Extension and Application Repository).


* * *

## SPL


* Standard PHP Library (Biblioteca Padrão do PHP)
* Extensões disponíveis e compiladas no PHP 5 por padrão
* Melhorias no PHP 5.1
* <http://www.php.net/~helly/php/ext/spl/>
* `ArrayAccess` interface
   * `function offsetSet($offset, $value);`
   * `function offsetGet($offset);`
   * `function offsetUnset($offset);`
   * `function offsetExists($offset);`
* `Iterator` interface
   * `function current();`
   * `function next();`
   * `function rewind();`
   * `function key();`
   * `function valid();`
* `SeekableIterator` interface
   * `Iterator`
   * `function seek($index);`
* `RecursiveIterator` interface
   * `Iterator`
   * `public RecursiveIterator getChildren ( void )`
   * `public bool hasChildren ( void )`
* `FilterIterator`


* * *

## Reutilização de Código


* Nos solucionamos os mesmos problemas todos os dias
* Nos solucionamos os mesmos problemas que nossos vizinhos todos os dias
* Nos solucionamos os mesmos problemas a cada projetos
* Reutilização de Código permite a redução no tempo de desenvolvimento enquanto aumenta a qualidade do código

* * *

## Design Patterns (Padrões de Projeto)


* apresenta soluções bem definidas para problemas comuns
* fornece uma linguagem comum para os desenvolvedores


* * *

## Factory (Fabrica)


* is used to provide a common interface to a series of classes with identical functionality but different internals (think data storage, varying shipping systems, payment processing)
* The “factory” provides an instance of the appropriate class


* * *

## Singleton


* to ensure that you have only one instance of a given class at a time
* myriad of circumstances; resource connections (database, file, external) most notably
* Advised to be avoided lately


* * *

## Registry


An extension of the Singleton Pattern, that allows for differing functionality based on some input data


* * *

## Active Record


Encapsulates a data source, allowing external code to concentrate on using the data while the active record pattern provides a consistent interface, hiding the work that goes into iterating over records, making changes etc.


* * *

## MVC


* Model-View-Controller
* Complex pattern, the user initiates an action via the controller, which interfaces with the model, finally the view is called which takes care of dealing with the user interface
* allows for modularity in code