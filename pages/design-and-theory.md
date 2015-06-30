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

## Factory (Fábrica)

* é utilizada para fornecer uma interface comum para uma série de classes com funcionalidades idênticas mas internamente diferentes
* A "fábrica" fornece uma instância apropriada da classe


* * *

## Singleton

* para garantir que você tenha apenas uma instância de uma determinada classe de cada vez
* infinidade de circunstâncias; conexões de recursos (banco de dados, arquivo, externos) especialmente
* ultimamente é aconselhável evita-lo


* * *

## Registry

Uma extensão do padrão Singleton, que permite funcionalidades diferentes com base em alguns dados de entrada


* * *

## Active Record

Encapsula uma fonte de dados, permitindo que o código externo se concentre na utilização dos dados enquanto o padrão "Active Record" fornece uma interface consistente, ocultando o trabalho de iteração sobre registros, realização de mudanças, etc.


* * *

## MVC


* Model-View-Controller
* Um padrão complexo, o usuário inicia uma ação através do "Controller", que faz interface com o modelo, e finalmente a visualização é chamada, cuidando de lidar com a interface gráfica do usuário
* permite a modularidade no código
