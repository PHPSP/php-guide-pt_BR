---
layout: page
title: "Strings e Padrões"
description: ""
---
{% include JB/setup %}

{% include menu/strings-and-patterns.md %}

* * *

## Funções {#funcoes}


* `int strlen ( string $string )`
* `int strpos ( string $haystack , mixed $needle [, int $offset = 0 ] )` - retorna a posição do trecho pesquisado ("agulha") dentro de um texto maior ("palheiro")
* `int stripos ( string $haystack, string $needle [, int $offset] )`
* `int strrpos ( string $haystack, string $needle [, int $offset] )`
* `string strstr ( string $haystack , mixed $needle [, bool $before_needle = false ] )` - retorna o trecho pesquisado desde o início da primeira ocorrência até o fim
* `string stristr ( string $haystack, string $needle )`
* `int strspn ( string $subject , string $mask [, int $start [, int $length ]] )` - retorna o número de caracteres correspondentes à máscara
* `int strcspn ( string $str1 , string $str2 [, int $start [, int $length ]] )` - usa uma lista negra ("blacklist") e retorna os caracteres não encontrados na lista
* `string setlocale ( int $category, string $locale [, string $...] )`
* `string str_pad ( string $input , int $pad_length [, string $pad_string = " " [, int $pad_type = STR_PAD_RIGHT ]] )`
* `string strrev ( string $string )` - Inverte um texto


* * *

## Sequências de escape {#sequencias_de_escape}


* `\n` avanço de linha (LF or 0x0A (10) in ASCII)
* `\r` retorno de carro (CR or 0x0D (13) in ASCII)
* `\t` tabulação horizontal (HT or 0x09 (9) in ASCII)
* `\\` contrabarra
* `\$` cifrão
* `\"` aspas duplas
* `\[0-7]{1,3}` a sequência de caracteres correspondentes a essa expressão regular é um caractere na notação octal


* * *

## Correspondência de Strings {#correspondencia_de_strings}


* `int strcmp ( string $str1 , string $str2 )` - Retorna < 0 se str1 é menor que str2 ; > 0 se str1 é maior que str2, e 0 se forem iguais.
* `int strcasecmp ( string $str1 , string $str2 )` – versão da função strcmp() sem distinção entre maiúsculas e minúsculas
* `int strncasecmp ( string $str1 , string $str2 , int $len )`
* `0 == FALSE` e `0 !== FALSE`


* * *

## Extração {#extracao}


* `string substr ( string $string , int $start [, int $length ] )` - para obter uma porção de uma string
* Sintaxe de Array
* A sintaxe `{}` foi descontinuada no PHP 5.1 e irá disparar um erro do tipo `E_STRICT`


* * *

## Formatação {#formatacao}


* algumas vezes, deve-se levar em conta sua localização
* `string number_format ( float $number , int $decimals , string $dec_point , string $thousands_sep )` – por padrão, formata um número usando vírgulas como separador de milhares e nenhum decimal
* `string money_format ( string $format , float $number )` – apenas disponível quando a biblioteca C `strfmon()` está no sistema (windows não possui)


* * *

## Família Print {#familia_print}


* `int print ( string $arg )` - Imprime arg. (construção da linguagem)
* `int printf ( string $format [, mixed $args [, mixed $... ]] )` - Imprime uma string formatada
* `string sprintf ( string $format [, mixed $args [, mixed $... ]] )` - Retorna uma string formatada
* `int vprintf ( string $format , array $args )` - Mostra valores de um array como uma string formatada de acordo com um formato
* `mixed sscanf ( string $str , string $format [, mixed &$... ] )` - http://php.net/manual/pt_BR/function.sscanf.php
* `mixed fscanf ( resource $handle , string $format [, mixed &$... ] )` - Interpreta uma entrada de dados via arquivo de acordo com um formato


* * *

## Especificadores de Formatação da função Printf {#especificadores_formatacao_funcao_printf}

* `%` - um caractere literal de porcentagem. Nenhum argumento é necessário.
* `b` - o argumento é tratado como um inteiro e mostrado como um número binário.
* `c` - o argumento é tratado como um inteiro e mostrado como o caractere correspondente ao seu valor ASCII.
* `d` - o argumento é tratado como um inteiro e mostrado como um número decimal (com sinal).
* `e` - o argumento é tratado como uma notação científica (e.g. `1.2e+2`).
* `u` - o argumento é tratado como um inteiro e mostrado como um número decimal sem sinal.
* `f` - o argumento é tratado como um número real (float) e mostrado como um número de ponto flutuante (baseado na localização).
* `F` - o argumento é tratado como um número real (float) e mostrado como um número de ponto flutuante (não baseado na localização). Disponível desde as versões do PHP 4.3.10 e do PHP 5.0.3.
* `o` - o argumento é tratado como um inteiro e mostrado como um número octal.
* `s` - o argumento é tratado e mostrado como uma string.
* `x` - o argumento é tratado como um inteiro e mostrado como um número hexadecimal (em letras minúsculas).
* `X` - o argumento é tratado como um inteiro e mostrado como um número hexadecimal (em letras maiúsculas).


* * *

## Substituição {#substituicao}

* `mixed str_replace ( mixed $search , mixed $replace , mixed $subject [, int &$count ] )`
* `mixed str_ireplace ( mixed $search, mixed $replace, mixed $subject [, int &$count] )`
* `mixed substr_replace ( mixed $string, string $replacement, int $start [, int $length] )`
* `string strtr ( string $str, string $from, string $to )`


* * *

## PCRE – Meta Caracteres {#pcre_meta_caracteres}

PCRE (Expressões Regulares Compatíveis com Perl, do inglês, Perl Compatible Regular Expressions).

* `\d` Dígitos 0-9
* `\D` Tudo que não seja um dígito
* `\w` Qualquer caractere alfanumérico ou um underline (_)
* `\W` Qualquer caractere que não seja alfanumérico ou um underline
* `\s` Qualquer espaço em branco (espaços, tabulações, quebras de linha)
* `\S` Qualquer caractere que não seja um espaço em branco
* `.` Qualquer caractere exceto uma quebra de linha
* `?` Ocorre nenhuma (0) ou uma (1) vez
* `*` Ocorre nenhuma (0) ou mais vezes
* `+` Ocorre uma (1) ou mais vezes
* `{n}` Ocorre exatamente n vezes
* `{,n}` Ocorre no máximo n vezes
* `{m,}` Ocorre m ou mais vezes
* `{m,n}` Ocorre entre m e n vezes


* * *

## PCRE – Modificadores de Padrão {#pcre_modificadores_de_padrao}


* `i` – Busca sem distinção entre maiúsculas e minúsculas
* `m` – Multilinha, $ e ^ irão "casar" com quebras de linhas
* `s` – Faz com que o metacaractere ponto "case" com quebras de linha
* `x` – Permite comentários
* `U` – Torna o motor de busca "não-guloso"
* `u` – Liga o suporte ao UTF8
* `e` – Permite executar as correspondências feitas com a função preg_replace() (marcado como obsoleto no PHP 5.5.0 e removido no PHP 7. Como alternativa, usar preg_replace_callback())

* `int preg_match ( string $pattern , string $subject [, array &$matches [, int $flags [, int $offset ]]] )` – Retorna o número de correspondências encontradas com base num texto de busca
* `int preg_match_all ( string $pattern, string $subject, array &$matches [, int $flags [, int $offset]] )`
* `mixed preg_replace ( mixed $pattern , mixed $replacement , mixed $subject [, int $limit = -1 [, int &$count ]] )`
* `array preg_split ( string $pattern , string $subject [, int $limit = -1 [, int $flags = 0 ]] )`


* * *

## HEREDOC e NOWDOC {#heredoc_e_nowdoc}

[http://php.net/manual/pt_BR/language.types.string.php#language.types.string.syntax.heredoc](http://php.net/manual/pt_BR/language.types.string.php#language.types.string.syntax.heredoc)

A partir do PHP 5.3.0, é possível inicializar variáveis estáticas além de propriedades e constantes de uma classe usando a sintaxe Heredoc.

O PHP 5.3.0 também introduz a possibilidade de que os Heredocs usem aspas duplas em suas declarações.

Os Heredocs, em geral, não podiam ser utilizados para inicializar propriedades de classe. Desde o PHP 5.3 essa limitação é válida apenas para os heredocs que contenham variáveis.

{% highlight php5 linenos %}
<?php
$str = <<<EOD
Exemplo de um texto
apresentado em múltiplas linhas
utilizando a sintaxe heredoc.
EOD;

/* Exemplo mais complexo, com variáveis. */
class foo
{
    var $foo;
    var $bar;

    function foo()
    {
        $this->foo = 'Foo';
        $this->bar = array('Bar1', 'Bar2', 'Bar3');
    }
}

$foo = new foo();
$nome = 'MeuNome';

echo <<<EOT
Meu nome é "$nome". Estou imprimindo algum $foo->foo.
Agora, estou imprimindo algum {$foo->bar[1]}.
Deveria ser impressa uma letra 'A' maiúscula: \x41
EOT;
?>
{% endhighlight %}

[http://php.net/manual/pt_BR/language.types.string.php#language.types.string.syntax.nowdoc](http://php.net/manual/pt_BR/language.types.string.php#language.types.string.syntax.nowdoc)

Diferente dos heredocs, os nowdocs podem ser usados em qualquer contexto de dados estáticos. O exemplo típico é a inicialização de propriedades de classe ou constantes.

Um nowdoc é especificado de forma similar a um heredoc, mas nenhum tipo de interpretação é feita dentro de um nowdoc.

Um nowdoc começa com a mesma sequência `<<<` usada para os heredocs, mas o identificador é embutido em aspas simples, e.g. `<<<'EOT'`. Todas as regras dos identificadores heredoc também se aplicam aos nowdoc, especialmente aquelas referentes à aparência do identificador de fechamento.
