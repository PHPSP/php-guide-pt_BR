---
layout: page
title: "Php Basics"
description: ""
---
{% include JB/setup %}

{% include menu/php-basics.md %}

## Tags PHP 

Tags Padrão – melhor solução para portabilidade e compatibilidade com versões anteriores
pois é garantido que sempre serão válidas e não podem ser desabilitadas através do arquivo de configuração.

{% highlight php5 linenos %}
<?php 
... code
?>
{% endhighlight %}

No entanto, pode haver apenas uma tag aberta no início da página `<?php `.

Tags Curtas - podem ser desabilitadas (normalmente por compatibilidade com XML) na diretiva `short_open_tag`
do php.ini:

{% highlight php5 linenos %}
<?
... code
?>
{% endhighlight %}

Essa variação de tags curtas é idêntica a `<? echo`:
{% highlight php5 %}
<?=$variable ?>
{% endhighlight %}

Tags de script também possuem garantia de serem válidas, assim como as tags padrão: 

{% highlight html linenos %}
<script language="php">
... code
</script>
{% endhighlight %}

Tags ASP - é necessário serem especificamente habilitadas no php.ini através da diretiva `asp_tags`:

{% highlight php5 linenos %}
<%
... code
%>
<%=$variable; %>
{% endhighlight %}

* * *

## Comentários

O "comentário de uma linha" somente comenta até o final da linha ou o bloco de código PHP 
atual, o que vier primeiro. Isso significa que, um código HTML depois de `// ... ?>` ou `# ... ?>`
será impresso. `?>` finaliza o modo PHP e retorna para modo HTML e // ou # não influenciam nisso.
Se a diretiva `asp_tags` no arquivo de configuração estiver habilitada, o mesmo acontecerá com `// %>` e `# %>`. 
Porém a tag `</script>` não finaliza o modo PHP se a linha estiver comentada.

{% highlight php5 linenos %}
<?php
// Este é um comentário de uma linha

# Este também é um comentário de uma linha 
# Novo comentário de uma linha ?> Aqui o comentário de uma linha não funciona e isso será impresso
{% endhighlight %}

Comentário de diversas linhas termina na primeira ocorrência de `*/`. Preste atenção em não emendar mais de um bloco 
de comentários de diversas linhas e também em não utilizar `*/` antes do termino do comentário, é comum cometer este erro 
se você está tentando comentar um bloco grande de código.

{% highlight php5 linenos %}
<?php
/*
Este é um comentário de 
diversas linhas
*/

/* isso também está 
comentado */ mas isso não está */
?>
{% endhighlight %}

Abaixo você encontrará um exemplo DocComment. Para o PHP é como um comentário normal. 
Para maiores informações você pode visitar o site [phpDocumentor](http://www.phpdoc.org/)

{% highlight php5 linenos %}
<?php
/**
* Exemplo de documentação de API
*
* @param string $bar
*/
function foo($bar) { }
?>
{% endhighlight %}

* * *

## Operadores

Um operador é algo que interage um ou mais valores (ou expressões, no jargão da programação) 
e então devolve outro valor. De forma que a própria construção se torna uma expressão.

Operadores podem ser agrupados de acordo com o número de valores que estes operam.
Há três tipos de operadores. Os operadores unários operam em apenas um valor, por 
exemplo, ! (operador de negação) ou o ++ (operador de incremento). 
Operadores binários operam em dois valores, por exemplo, os operadores aritméticos 
`+` (adição), `-` (subtração), entre outros, já que este é o grupo que contém a maioria 
dos operadores que o PHP suporta.
O terceiro grupo é do operador ternário `? :`, que opera em três valores. Este é geralmente 
chamado de "o operador ternário", porém, talvez fosse mais apropriado ser chamado de operador 
condicional. 

A precedência de um operador especifica qual é a prioridade deste.
Por exemplo, na expressão `1 + 5 * 3`, a resposta é 16 e não 18 pois o operador de 
multiplicação (`*`) tem prioridade maior do que o operador de adição (`+`).
Parênteses podem ser utilizados para forçar a precedência, se necessário. Por exemplo: 
o resultado de `(1 + 5) * 3` será 18.

Quando os operadores possuem a mesma precedência, sua associatividade decide se eles
são avaliados a partir da direita, ou a partir da esquerda.

Para o entendimento da precedência dos operadores, veja a tabela no 
[Manual do PHP](http://php.net/manual/pt_BR/language.operators.precedence.php)

### Operadores aritméticos

Funciona da mesma forma que no mundo real:

{% highlight php5 linenos %}
<?php

echo 2 + 2; // Adição. Vai imprimir 4
echo 3 - 2; // Subtração. Vai imprimir 1
echo 1 * 2; // Multiplicação. Vai imprimir 2
echo 4 / 2; // Divisão . Vai imprimir 2
echo -2; // Negação. Vai imprimir -2
echo 3 % 2 // Módulo (resto da divisão). Vai imprimir 1

?>
{% endhighlight %}

O operador da divisão `/` retorna um valor com ponto flutuante, a não ser que 
os dois operandos sejam inteiros (ou strings que são convertidas para inteiros) 
e os números sejam inteiramente divisíveis, neste caso um inteiro é retornado.
Se você tentar dividir algum valor por zero, o PHP irá exibir um aviso: 
`PHP Warning: Division by zero`.

Operandos de módulo são convertidos para inteiros (removendo a parte decimal) 
antes de processar.

O resultado do operador módulo % tem o mesmo sinal (negativo ou positivo) que 
o valor que está sendo dividido, ou seja, o resultado de $a % $b terá o mesmo 
sinal de $a.

### Operadores de atribuição

O operador básico de atribuição é "=". Isso significa que o operando da esquerda
recebe o valor do operando da direita, ou seja, o da esquerda é configurado com
o valor da direita. 

O valor de uma expressão de atribuição é o valor atribuído. Isso é, o valor de `$a`
na expressão `$a = 3` será igual a 3.

Para arrays, a atribuição de um valor a uma chave é feita utilizando o operador `=>`. A 
precedência deste operador é a mesma que outros operadores de atribuição.

Além do operador básico de atribuição, há "operadores combinados" para todos os 
operadores aritméticos, de array e string que permitem a você pegar um valor de 
uma expressão e então usar aquele valor para o resultado daquela expressão.
Por exemplo:

{% highlight php5 linenos %}
<?php
$a = 3;
$a += 5; // Igual a 8
?>
{% endhighlight %}

Note que a atribuição copia a variável original para a nova (atribuição por valor),
assim a mudança de uma não afeta a outra.

#### Atribuição por referência

Atribuição por referência também é suportado pelo PHP, utilizando a sintaxe 
`$var = &$othervar;` (`&` E comercial antes da variável). Atribuição por referência
significa que ambas as variáveis estarão apontando para o mesmo conteúdo, não será 
apenas uma cópia. 

{% highlight php5 linenos %}
<?php
$a = 3;
$b = &$a; // $b é uma referência de $a

print "$a\n"; // imprime 3
print "$b\n"; // imprime 3

$a = 4; // altera $a

print "$a\n"; // imprime 4
print "$b\n"; // imprime 4 também, pois $b é uma referência de $a
?>
{% endhighlight %}

Desde o PHP 5, o operador "new" retorna referência automaticamente, 
então usar o resultado de "new" por referência resulta em uma mensagem  **E_DEPRECATED** 
desde o PHP 5.3.

Mais informações sobre referências a seu potencial de utilização podem ser encontrados
na seção de [Referências](http://php.net/manual/pt_BR/language.references.php) do manual.

### Operador bit-a-bit

Operadores bit-a-bit permitem que você avalie e manipule bits específicos dentro 
de um inteiro. Números integrais são internamente convertidos para bits:
`5 -> 0101 = 0*8 + 1*4 + 0*2 + 1*1`

Bit shifting in PHP is arithmetic. Bits shifted off either end are discarded. Left shifts 
have zeros shifted in on the right while the sign bit is shifted out on the left, meaning 
the sign of an operand is not preserved. Right shifts have copies of the sign bit shifted 
in on the left, meaning the sign of an operand is preserved.

Utilize parênteses para ter certeza da precedência desejada. Por exemplo, 
`$a & $b == true` avalia a equivalência  e então o operador bit-a-bit; 
enquanto `($a & $b) == true` avalia bit-a-bit e então a equivalência.

Se ambos os parâmetros da esquerda e da direita forem strings, esses operadores 
irão trabalhar nos valores ASCII dos caracteres.

* `$a & $b` (E) — Os bits que estão ativos tanto em $a quanto em $b são ativados.
* `$a | $b` (OU) — Os bits que estão ativos em $a ou em $b são ativados.
Pelo menos `1`.
* `$a ^ $b` (XOR) — Os bits que estão ativos em $a ou em $b, mas não em ambos, 
são ativados.
* `~ $a` (NÃO) — Os bits que estão ativos em $a não são ativados, e vice-versa. 
Converter `0` em `1` e `1` em `0`
* `>>` (Deslocamento à direita) – Desloca os bits de $a $b passos para a direita, 
completando as casas descolacas com 0.
(cada passo significa "divide por dois")
* `<<` (Deslocamento à esquerda) – Desloca os bits de $a $b passos para a esquerda, 
completando as casas descolacas com 0. 
(cada passo significa "multiplica por dois")

Para mais informações sobre conversão e exemplos, dê uma olhada no 
[Manual do php](http://php.net/manual/pt_BR/language.operators.bitwise.php)

### Operadores de comparação

Operadores de comparação, como diz o nome, permite a comparação de dois valores.

* `$a == $b` (IGUAL) — **TRUE** se $a é igual a $b após a coerção destes valores.
* `$a === $b` (IDÊNTICO) — **TRUE** se $a é igual a $b e eles possuam o mesmo tipo
* `$a != $b` `$a <> $b` (DIFERENTE) — **TRUE** se $a é diferente de $b após a coerção 
destes valores.
* `$a !== $b` (NÃO IDÊNTICO) — **TRUE** se $a é diferente de $b ou se eles não 
possuem o mesmo tipo.
* `$a < $b` (MENOR QUE) — **TRUE** se $a é menor que $b após a coerção.
* `$a > $b` (MAIOR QUE) — **TRUE** se $a é maior que $b.
* `$a <= $b` (MENOR OU IGUAL A) — **TRUE** se $a é menor ou igual a $b.
* `$a >= $b` (MAIOR OU IGUAL A) — **TRUE** se $a maior ou igual a $b.

Se você comparar um número com uma string ou se a comparação envolve strings 
numéricas, então cada string é convertida para um número e a comparação é feita 
numericamente. A conversão de tipo não acontece quando a comparação é feita com
`===` ou `!==` pois essas comparações envolvem também o tipo.

Para vários tipos, a comparação é feita de acordo com os exemplos abaixo:

* `null` para `string` — Converte NULL para "", ou em outras palavras, para uma 
string vazia.
* `bool ou null` para qualquer tipo — Converte para `bool`
* `object` para `object` — Quando estiver usando o operador de comparação `==`, 
variáveis objeto são comparadas de maneira simples, nominalmente: Duas instâncias 
de objetos são iguais se tem os mesmos atributos e valores e se são instâncias da 
mesma classe. Por outro lado, quando estiver usando o operador `===` (idêntico),
variáveis objeto são idênticos somente se eles tem referência a mesma instância
da mesma classe.
* `string, resource ou number` para `string, resource ou number` — Transforma 
strings e resources para numbers
* `array` para `array` — Array com menos membros é menor, se a chave do operando 1 
não é encontrada no operando 2, então os arrays são incomparáveis, caso contrário, 
compara valor por valor
* `array`  para qualquer tipo — array é sempre maior
* `object` para qualquer tipo — object é sempre maior.

**Aviso**: Por causa da forma que os números de ponto flutuante são representados 
internamente, você não deve testar a igualdade de dois números de ponto flutuante.
Para maiores informações, veja a documentação para 
[número de ponto flutuante](http://php.net/manual/pt_BR/language.types.float.php) 

#### Operador ternário

Outro operador condicional é o `?:` (ou ternário). A expressão `(expr1) ? (expr2) : (expr3)`
resulta em expr2 se expr1 for **TRUE** e em expr3 se expr1 for **FALSE**. Desde 
o PHP 5.3 é possível deixar de fora a parte do meio do operador ternário. A
expressão `expr1 ?: expr3` retorna expr1 se expr1 for **TRUE**, caso contrário,
retorna expr3.

Note que o operador ternário é uma afirmação e que não avalia para uma variável, mas
sim para o resultado da afirmação. É importante saber disso caso você queira retornar 
uma variável por referência. Portanto, a expressão `return $var == 42 ? $a : $b;` em 
uma função com retorno por referência não irá funcionar e, nas novas versões do PHP, 
um alerta ocorrerá.

É recomendado evitar o empilhamento de expressões ternárias. O comportamento do
PHP, quando utilizado mais de um operador ternário em uma única expressão, não é 
óbvio.

### Operadores de controle de erro

O PHP suporta um operador de controle de erro: o sinal `@`. Quando ele precede 
uma expressão em PHP, qualquer mensagem de erro que possa ser gerada por aquela 
expressão será ignorada.

Se você tem uma função de erro customizada com `set_error_handler()`, ela ainda será 
chamada, porém essa função customizada pode (e deve) chamar `error_reporting()`,
que irá retornar 0 quando a chamada tiver sido precedida por um `@`.

Se o recurso `track_errors` estiver habilitado, qualquer mensagem de erro gerada 
pela expressão será gravada na variável `$php_errormsg`. Esta variável será 
sobrescrita em cada erro.

**Nota**: O `@` funciona somente em expressões. Uma regra simples para lembrar disso: 
se você pode pegar o valor de alguma coisa, você pode prefixar isso com o @. Assim, 
você pode prefixar chamadas de variáveis, funções e includes, constantes e afins. 
Você não pode prefixar definições de funções ou classe, estruturas condicionais como 
o if, foreach e assim por diante.

**Aviso**: Atualmente, o operador de controle de erro "@" sempre desativa mensagens 
de erro, mesmo para erros críticos, que terminam a execução de scripts. Além de outras 
coisas, isto significa que se você usar "@" para suprimir erros de certas funções e 
elas não estiverem disponíveis ou com tipos incorretos, o script vai parar exatamente 
aí sem nenhuma indicação da razão.

### Operadores de execução

O PHP suporta um operador de execução: acentos graves (`` ` ` ``). O PHP tentará 
executar o conteúdo dos acentos graves como um comando do shell; a saída será 
retornada (isto é, ela não será simplesmente descarregada para a saída; ela 
pode ser atribuída a uma variável). A utilização do operador acentos graves 
é idêntica a função shell_exec(). Por exemplo:

{% highlight php5 linenos %}
<?php
$ls = `ls -la`;
print_r($ls); // irá imprimir o retorno do comando ls
?>
{% endhighlight %}

### Operadores de Incremento/Decremento

O PHP suporta operadores de pré e pós-incremento e decremento no estilo C.

* `++$a` (pré-incremento) — Incrementa 1 em `$a`, e então retorna `$a`
* `$a++` (pós-incremento) — Retorna `$a`, e então incrementa 1.
* `--$a` (pré-decremento) — o mesmo que pré-incremento, mas decrementa
* `$a--` (pó-decremento) — o mesmo que pós-increment, mas decrementa

O PHP segue a convenção Perl quando tratando-se de operações aritméticas 
em variáveis de caracteres. Por exemplo, em Perl $a = 'Z'; $a++; o $a se torna 
'AA'. Note que variáveis de caracteres podem ser incrementadas mas não 
decrementadas e somente caracteres "plain ASCII (a-z e A-Z)" são suportados.
Incrementar/Decrementar outras variáveis de caracteres não resultam em nada, 
a string original não é alterada.

**Note**: Os operadores de incremento/decremento não afetam valores booleanos.
Decrementar um valor NULL também não tem efeito algum, mas incrementar resulta 
em 1.

### Operadores lógicos

* `$a and $b` (E) — TRUE se ambos `$a` e `$b` são TRUE.
* `$a or $b` (OU) — TRUE se `$a` ou `$b` é TRUE.
* `$a xor $b` (Xor) — TRUE se `$a` ou `$b` é TRUE, mas não os dois.
* `! $a` (NÃO) — TRUE se `$a` não é TRUE.
* `$a && $b` (E) — TRUE se ambos `$a` e `$b` são TRUE.
* `$a || $b` (OU) — TRUE se `$a` ou `$b` for TRUE.

A razão para haver dois diferentes operadores para *and* e *or* é que eles 
operam em diferentes precedências, `&&` e `||`  possuem um nível de prioridade
maior do que `and` e `or`.

### Operadores de string

Há dois operadores de string. O primeiro é o operador de concatenação `.`, que 
retorna a concatenação dos seus argumentos da direita e da esquerda. O segundo 
é o operador de atribuição de concatenação `.=`, que acrescenta o argumento do 
lado direito no argumento do lado esquerdo. 

### Operadores de array

* `$a + $b` (União) — União de `$a` e `$b`.
* `$a == $b` (Igualdade) — TRUE se $a e $b possuam o mesmo par de chave/valor.
* `$a === $b` (Identidade) — TRUE se $a e $b tem os mesmos pares de chave/valor 
na mesma ordem e do mesmo tipo.
* `$a != $b` (Desigualdade) — TRUE se $a não é igual a $b.
* `$a <> $b` (Desigualdade) — TRUE se $a não é igual a $b.
* `$a !== $b` (Não identidade) — TRUE se $a não é idêntico a $b.

O operador + acrescenta os elementos da direita no array da esquerda. Para chaves 
que existem nos dois arrays, os elementos do array da esquerda serão utilizados e 
elementos iguais do array do lado direito serão ignorados

### Operadores de tipo

`Instanceof` – Retorna true se a variável indicada é uma instância de alguma classe 
designada, de uma de suas sub-classes ou de uma interface.

* * *

## Variáveis

### Nomenclatura:

* Só pode conter letras, números ou sublinhado (underscore)
* Obrigatoriamente se inicia com letra ou sublinhado (underscore)

### Tipos

* Tipos escalares: booleano, string, inteiro, números com ponto flutuante.
* Tipos compostos: array, objeto.
* Tipos especiais: resource, null.

### Strings

Cada caractere é representado por um único byte. PHP não possui suporte nativo para 
caracteres de configuração multi-byte (como Unicode)

Coleções ordenadas de dados binários.

Pode ser citado em uma das três maneiras:

* `'algum texto'` - caracteres com aspas simples serão gravados da forma que são, não 
interpretará ou substituirá variáveis ou sequência de escapes 
* `"algum texto"` – com aspas duplas as variáveis e sequência de escapes serão interpretadas e substituídas
* `<<<` – Heredoc é uma maneira similar a aspas duplas, mas foi feito para ser utilizada com diversas linhas
e permite o uso de aspas sem necessitar de escape.

{% highlight php5 linenos %}
<?php
$greeting = <<<GREETING
She said "That is $name's" dog!
While running towards the thief
GREETING;
{% endhighlight %}

### Inteiro

Pode ser especificado como decimal (base 10), hexadecimal (base 16, precedido por um 0x), ou octal (base 8, precedido por um 0) 
opcionalmente precedido por um sinal (+, -)

O tamanho máximo de um inteiro depende da plataforma, um máximo de ~2Bilhões é comum

### Número de ponto flutuante

`1.234, 1.2e3, 7E-10`

O tamanho de um número de ponto flutuante depende da plataforma, porém um máximo de `~1.8e308` 
com a precisão de aproximadamente 
14 dígitos decimais é um valor comum. 

### Booleano

* Qualquer número inteiro que não seja 0 (zero) é considerado TRUE
* TRUE e FALSE são case-insensitive e tanto a representação em caixa alta quanto em caixa baixa são comuns.

### Arrays

Arrays podem conter qualquer combinação de outros tipos de variáveis, até arrays ou objetos.

### Objects (Objetos)

Objetos permitem que dados e métodos sejam combinados em uma estrutura coesa.

### Resource

Variável especial que representa um tipo de recurso externo, geralmente um arquivo aberto ou a 
conexão com um banco de dados.

Enquanto variáveis do tipo resource podem ser impressas, sua única utilização sensata é com as 
funções projetadas para trabalhar com elas.

### null

* Não tem valor e não tem tipo
* Não é o mesmo que o inteiro 0 (zero) ou que uma string vazia, já que estes têm um tipo

### Variáveis variáveis

{% highlight php5 linenos %}
<?php
$a = 'nome';
$$a = "Paul";
echo $nome; //Paul
{% endhighlight %}

* * *

## Constantes

Não podem ser alteradas após serem configuradas.

{% highlight php5 linenos %}
<?php
define('ERROR', 'Algo deu errado.');
const FOO = 'bar';
{% endhighlight %}

Apenas escalar.

* * *

## Estruturas de controle

### If

Alternado:

{% highlight php5 linenos %}
<?php
if ():
  ... 
else: 
  ... 
elseif:
  ... 
endif;
{% endhighlight %}

Encurtado:

{% highlight php5 linenos %}
<?php
$expr ? true : false)
{% endhighlight %}

### switch

### while

### do

### for

continue

break

### foreach

### functions

Parâmetros:

* Opcional
* Por referência
* Por valor
* Objetos
* Funções variáveis

### Objetos

* * *

## Construção da linguagem

Elementos que estão incorporados na língua.

Não tem retorno de valor.

{% highlight php5 linenos %}
<?php
echo 'alguma coisa'; 
die();
exit();
{% endhighlight %}

Finalizar um script em PHP5:

{% highlight php5 linenos %}
<?php
__halt_compiler()
die();
exit();
{% endhighlight %}

* * *

## Namespaces

[http://php.net/manual/pt_BR/language.namespaces.php](http://php.net/manual/pt_BR/language.namespaces.php)

Resolve dois problemas:

* Conflito de nomes entre o código que você cria e em classes/functions/constants internas 
do PHP ou classes/funções/constantes de terceiros.
* Possibilidade de utilizar um apelido ou de diminuir o nome de classes/functions/constants  
com o nome muito grande pelo intuito de prevenir conflitos de nomes

Somente três tipos de unidades de códigos são afetadas por namespaces:

* classes
* funções (functions)
* constantes (constants). 

Um arquivo de código que possua um namespace deve declarar o mesmo no início do arquivo, 
antes de qualquer código - com uma exceção: a palavra chave [declare](http://php.net/manual/pt_BR/control-structures.declare.php).

Namespaces podem ser definidos com sub níveis.

Uma classe pode ser referenciada em três formas:

1. Nome não classificado ou nome de classe não pré-fixado, como `$a = new foo();` ou 
`foo::staticmethod();`. Se o atual namespace for `currentnamespace`, isso implicará em 
`currentnamespace\foo`. Se o código for global, sem definição de namespace, isso implicará em 
`foo`. Apenas um detalhe: nomes não qualificados para funções e constantes irá acarretar em 
funções e constantes globais caso o namespace da função ou constante não for definida. Veja
[Utilizando namespaces: fallback para global function/constant](http://php.net/manual/pt_BR/language.namespaces.fallback.php) 
para mais detalhes.
2. Nome qualificado ou nome de classe pré-definido, como `$a = new subnamespace\foo();` ou 
`subnamespace\foo::staticmethod();`. Se o atual namespace for `currentnamespace`, 
isso implicará em `currentnamespace\subnamespace\foo`.Se o código for global, código sem 
namespace, isso implicará em `subnamespace\foo`.
3. Nomes totalmente classificados, ou um nome pré fixado com prefixo global, como
`$a = new \currentnamespace\foo();` ou `\currentnamespace\foo::staticmethod();`. Isso sempre 
implica no nome literal especificado no código, `currentnamespace\foo`.

Duas formas de apelidar ou importar: apelidar o nome da classe e apelidar o namespace.

{% highlight php5 linenos %}
<?php
namespace meu\nome; // veja "Definindo namespace" 

class MyClass {}
function myfunction() {}
const MYCONST = 1;

$a = new MyClass;
$c = new \meu\nome\MyClass; // veja "Global Space"

$a = strlen('hi'); // veja "Utilizando namespaces: fallback para global
                   // function/constant"

$d = namespace\MYCONST; // veja "operador namespace e __NAMESPACE__
                        // constant"
$d = __NAMESPACE__ . '\MYCONST';
echo constant($d); // veja "Namespaces e características dinâmicas da linguagem"
?>
{% endhighlight %}

{% highlight php5 linenos %}
<?php
namespace foo;
use My\Full\Classname as Another;

// isso é a mesma coisa que usar My\Full\NSname as NSname
use My\Full\NSname;

// importar uma classe global
use \ArrayObject;

$obj = new namespace\Another; // instancia um objeto da classe foo\Another
$obj = new Another; // instancia um objeto da classe My\Full\Classname
NSname\subns\func(); // chama a função My\Full\NSname\subns\func
$a = new ArrayObject(array(1)); // instancia um objeto da classe ArrayObject
// sem o uso de "use \ArrayObject" estaríamos instanciando um objeto da classe foo\ArrayObject
?>
{% endhighlight %}

* * *

## Extensões

[http://devzone.zend.com/article/1021](http://devzone.zend.com/article/1021)

O pacote do PHP vem com aproximadamente 86 extensões, tendo uma média de 30 funções cada uma. Faça as contas, são aproximadamente 2500 funções. 
Como se não fosse o suficiente, [O repositório PECL](http://pecl.php.net/) oferece mais de 100 extensões adicionais, e muito mais pode ser encontrado pela internet

* * *

## Configuração

[http://php.net/manual/pt_BR/configure.about.php](http://php.net/manual/pt_BR/configure.about.php)

[http://php.net/manual/pt_BR/configuration.php](http://php.net/manual/pt_BR/configuration.php)

* * *

## Performance. Bytecode caching

