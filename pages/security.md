---
layout: page
title: "Segurança"
description: ""
---
{% include JB/setup %}

{% include menu/security.md %}

* * *

## Níveis


* Servidor Web
* Base de dados
* O próprio PHP


* * *

## Conceitos


* "Com grandes poderes vem grandes responsabilidades" (yeah)
* Defense in Depth - planeje falhas; aplicações permanecem mais resistentes com o tempo;
* Princípio do Privilégio Mínimo
* Termos: Validação vs "Escapar"
   * Validação ou Filtragem é o processo pelo qual você sujeita um dado a uma série de regras, este dado passará (será válido) ou não
   * "Escapar" - do inglês Escape - é o processo pelo qual você prepara um dado para um recurso específico, "escapando" algumas partes do dado para evitar confusão entre o que são instruções ou dados


* * *

## Valide Entradas


Uma das três coisas pode ser dita sobre dados recebidos:

* Ele é válido, o usuário enviou o dado que você quer, no formato em que você deseja
* Ele é inválido porque o usuário não seguiu ou entendeu as regras sobre o dado que você solicitou (i.e. Número telefônico mal formatado)
* Ele é inválido porque o usuário está tentando comprometer seu sistema

* Dados vindos do usuário final não podem ser confiados
* Valide os dados primeiro, não deixe a validação por ultimo
* Diga ao usuário o que ocorreu de errado o quanto antes
* Whitelist vs Blacklist


* * *

## Funções


* `bool ctype_alnum ( string $text )` - Verifica caracteres alfanuméricos
* `ctype_alpha` - Verifica caracteres alfabéticos
* `ctype_cntrl` - Verifica caracteres de controle
* `ctype_digit` - Verifica caracteres numéricos
* `ctype_graph` - Verifica por quaisquer caracteres possíveis de serem impressos, exceto espaço
* `ctype_lower` - Verifica caracteres em caixa baixa (letras minúsculas)
* `ctype_print` - Verifica por caracteres possíveis de serem impressos
* `ctype_punct` - Verifica por quaisquer caracteres que possam ser impressos, que não sejam espaço em branco ou alfanumérico
* `ctype_space` - Verifica caracteres de espaço em branco
* `ctype_upper` - Verifica caracteres em caixa alta (letras maiúsculas)
* `ctype_xdigit` - Verifica caracteres em hexadecimal


* * *

## Register Globals


* Register Globals era ótima, quando você estava aprendendo e mais ninguém via suas aplicações
* Sozinha não seria um risco à segurança; Combinada com códigos mal cuidados torna-se um problema
* Inicialize de antemão todas suas variáveis
* Codifique com o modo `E_STRICT` habilitado


* * *

## Magic Quotes


* Escapa automaticamente caracteres de aspas, barra invertida e null
* Depreciada no PHP 5.4
* Desabilitada por padrão no PHP 5
* Um pé no saco, você vai acabar com um código parecido com isto:

{% highlight php5 linenos %}
<?php
if (get_magic_quotes_gpc())
{
$string = stripslashes($string);
}
{% endhighlight %}


* * *

## Escapando (Escaping)


* `string strip_tags ( string $str [, string $allowable_tags ] )` – Remove de uma string qualquer coisa que se pareça com uma tag HTML
* `string htmlentities ( string $string [, int $quote_style = ENT_COMPAT [, string $charset [, bool $double_encode = true ]]] )` – Converte qualquer caractere que contenha uma entidade HTML específica
   * `ENT_COMPAT` - converte aspas duplas e não altera aspas simples
   * `ENT_QUOTES` - converte aspas duplas e simples
   * `ENT_NOQUOTES` - não converte as simples ou duplas
* `string htmlspecialchars ( string $string [, int $quote_style = ENT_COMPAT [, string $charset [, bool $double_encode = true ]]] )` – Converte `&, “, ‘, <, >` em suas respectivas entidades
* Escape seus dados ou use "prepared statements"


* * *

## XSS


* o agressor injeta código em sua página que contém um código que reescreve a página para fazer algo malicioso
* pode ser prevenido escapando e validando corretamente os dados


* * *

## CSRF


* um site explora a confiança do usuário em outro site para fazer algo acontecer
* iFrames


* * *

## Sessões


* Basicamente, combina cookies contendo um ID de sessão com um armazenamento local correspondente àquele ID de sessão
* Se o ID de sessão está comprometido, ou o armazenamento de dados não for seguro (/tmp numa máquina compartilhada), as sessões ainda são vulneráveis à ataques

* * *

## Fixação de Sessões


* um agressor engana um usuário a clicar em um link que fornece o ID de sessão, ou um usuário inocente cola um link contendo seu ID de sessão para alguém que não deveria o ter
* não permita que IDs de sessão venham por GET, e gere novamente IDs de sessão quando um usuário se autentica


* * *

## Espoliação de Sessão


* IDs de sessão são aleatórios
* Para defender-se, implemente algum tipo de identificação de navegador


* * *

## Injeção de Comandos


* O PHP fornece grandes poderes com as funções `exec()`, `system()` and `passthru()`, assim como o operador `\`` (acento grave)
* `string escapeshellcmd ( string $command )`
* `string escapeshellarg ( string $arg )`


* * *

## Configurações de Segurança


* `open_basedir` – Restringe o acesso a arquivos pelo PHP à um ou mais diretórios especificados
* `safe_mode` – limita o acesso a arquivos baseado no uid/gid do script em execução e o arquivo a ser acessado. Mais lento, não funciona bem com arquivos por upload.
* `disable_functions`
* `disable_classes`


* * *

## Encriptação, algorítmos de hash

* <http://php.net/manual/pt_BR/function.crypt.php>
* <http://php.net/manual/pt_BR/function.md5.php>
* <http://php.net/mcrypt>
* <http://php.net/mhash>


* * *

## Upload de arquivos

1. Defina permissão 755 para a pasta de upload
2. Verifique o arquivo usando funções PHP (se é um upload de foto, por exemplo)
3. Desabilite índices de diretórios e execução de scripts (utilizando .htaccess ou configurações de servidor)
4. Deixe a pasta de upload fora da raiz do site


* * *

## Armazenamento de dados



* * *

## SSL

<http://php.net/manual/pt_BR/book.openssl.php>
