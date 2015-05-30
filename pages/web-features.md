---
layout: page
title: "Recursos Web"
description: ""
---
{% include JB/setup %}

{% include menu/web-features.md %}


* * *

## EGPCS


* Variáveis de Ambiente (do inglês, **E**nvironment)
* **G**et
* **P**ost
* **C**ookie
* Variáveis de **S**ervidor e variáveis embutidas (do inglês, Server e Built-in)


* * *

## Formulários {#formularios}


* `GET` (recuperar) vs `POST` (enviar)
* Tokens em Formulários
* Valores Padrões
* Repopulação de dados
* `enctype=”multipart/form-data”` para arquivos
* `post_max_size`
* `max_input_time`
* `upload_max_filesize`
* `MAX_FILE_SIZE`
* `$_FILES[]`
   * `$_FILES['name']`
   * `$_FILES['type']`
   * `$_FILES['size']`
   * `$_FILES['tmp_name']`
   * `$_FILES['error']`


* * *

## Cookies


* Armazenamento de dados no lado do cliente (client side)
* Podem ser apagados, manipulados e copiados
* Tem comportamento inconsistente
* Permitem que suas aplicações armazenem uma pequena quantidade de dados em formato texto (geralmente de 4 a 6 kB) num cliente Web
* `header()` - Define os cookies de forma manual, usando a RFC para os cabeçalhos apropriados
* `setcookie()` - Encapsula a função Header, definindo valores padrões quando nada for passado.
* `$_COOKIE[]`
* Os valores do cookie precisam ser escalares.


* * *

## Sessões {#sessoes}


* Sessões, O modo mais seguro de guardar estado
* Usa um cookie que contém um Session ID
* Esse Session ID corresponde a um repositório de dados, geralmente local, que guarda a informação do usuário
* O Session ID é o único dado que é transmitido ao cliente, também sendo a única coisa que os identifica
* Session Hijacking e Session Fixation
* `session.use_trans_sid`
* `session.auto_start`
* `session_start()`
* `$_SESSION[]`
* `bool session_set_save_handler ( callback $open , callback $close , callback $read , callback $write , callback $destroy , callback $gc )`


* * *

## Cabeçalhos HTTP {#cabecalhos_http}


`void header ( string $string [, bool $replace = true [, int $http_response_code ]] )`

Redirecionamento

`header("Location: http://phparch.com");`

Outros cabeçalhos arbitrários

* Ataques de injeção de cabeçalhos
* Cache
   * `header(“Cache-Control: no-cache, must-revalidate”);`
   * `header(“Expires: Thu, 31 May 1984 04:35:00 GMT”);`
* Tipo de conteúdo (do inglês, Content-Type)
* Metadados (do inglês, Meta Information)

`bool headers_sent ([ string &$file [, int &$line ]] )`


* * *

## Compressão {#compressao}


* `ob_start("ob_gzhandler");`
* `zlib.output_compression = on`
* `zlib.output_compression_level = 9`


* * *

## Streams de entrada e saída PHP {#streams_de_entrada_e_saida_PHP}


* <http://php.net/manual/pt_BR/wrappers.php.php>
* `php://stdin` - `STDIN`
* `php://stdout` - `STDOUT`
* `php://stderr` - `STDERR`
* `php://output`
* `php://input`
* `php://filter` (disponível desde o PHP 5.0.0)
* `php://memory` (disponível desde o PHP 5.1.0)
* `php://temp` (disponível desde o PHP 5.1.0)


* * *

## Autenticação HTTP com PHP {#autenticacao_http_com_php}

* <http://php.net/manual/pt_BR/features.http-auth.php>
* `PHP_AUTH_USER`
* `PHP_AUTH_PW`
* `AUTH_TYPE`
