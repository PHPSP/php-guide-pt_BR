---
layout: page
title: "I/O"
description: ""
---
{% include JB/setup %}

{% include menu/io.md %}

* * *

## Arquivos


Fornecem um armazenamento simples, temporário ou permanente, para dados.

* `string file_get_contents ( string $filename [, bool $use_include_path = false [, resource $context [, int $offset = -1 [, int $maxlen = -1 ]]]] )`
* `int file_put_contents ( string $filename , mixed $data [, int $flags = 0 [, resource $context ]] )`
   * `FILE_USE_INCLUDE_PATH`
   * `FILE_APPEND`
   * `LOCK_EX`
* `$fp = fopen(__FILE__, 'r')`
* `string fread ( resource $handle , int $length )`
* `string fgets ( resource $handle [, int $length ] )`
* `int fwrite ( resource $handle , string $string [, int $length ] )`
* `array fstat ( resource $handle )`
* `array stat ( string $filename )`
* `bool fclose ( resource $handle )`
* `bool feof ( resource $handle )`


* * *

### Constantes


* `__LINE__`  A linha atual do arquivo.
* `__FILE__` O caminho completo com o nome do arquivo.
* `__FUNCTION__` O nome da função. (Adicionada no PHP 4.3.0) (diferencia maiúsculas e minúsculas)
* `__CLASS__` O nome da classe. (Adicionada no PHP 4.3.0) (diferencia maiúsculas e minúsculas)
* `__METHOD__` O nome do método da classe. (Adicionada no PHP 5.0.0) (diferencia maiúsculas e minúsculas)


* * *

### Modos dos Arquivos (File Modes) {#modos_dos_arquivos}


* `r` Abre apenas para leitura; coloca o ponteiro do arquivo no início dele.
* `r+` Abre para leitura e gravação; coloca o ponteiro do arquivo no início dele.
* `w` Abre apenas para gravação; coloca o ponteiro do arquivo no início dele, apagando todo seu conteúdo. Se o arquivo não existir, tenta criá-lo.
* `w+` Abre para leitura e gravação, coloca o ponteiro do arquivo no início dele, apagando todo seu conteúdo. Se o arquivo não existir, tenta criá-lo.
* `a` Abre apenas para gravação; coloca o ponteiro do arquivo no fim dele. Se o arquivo não existir, tenta criá-lo.
* `a+` Abre para leitura e gravação; coloca o ponteiro do arquivo no fim dele. Se o arquivo não existir, tenta criá-lo.
* `x` Cria e abre apenas para gravação; coloca o ponteiro do arquivo no início dele. Se o arquivo já existir, a execução da função fopen() falhará retornando FALSE e gerando um erro de nível `E_WARNING`. Se o arquivo não existir, tenta criá-lo.
* `x+` Cria e abre para leitura e gravação; coloca o ponteiro do arquivo no início dele. Se o arquivo já existir, a execução da função fopen() falhará retornando FALSE e gerando um erro de nível `E_WARNING`.

* * *

### Bloqueios


* `bool flock ( resource $handle , int $operation [, int &$wouldblock ] )`
   * `LOCK_SH` - aplica um bloqueio compartilhado (Shared)
   * `LOCK_EX` - aplica um bloqueio exclusivo/escrita (Exclusive)
   * `LOCK_UN` - libera um bloqueio
* A aplicação e remoção de bloqueios pode impactar a performance a medida que se aumenta o tráfego


* * *

### Funções de Arquivos {#funcoes_de_arquivos}


#### Controle de Acesso

Perceba que os resultados de uma chamada para qualquer uma dessas funções serão colocados em cache, dessa forma duas chamadas para determinada função na mesma cadeia de recursos e dentro do mesmo script retornarão o mesmo valor, não importando se o recurso tiver sido mudado nesse meio tempo.

* `is_dir($path);` // Retorna se o caminho é um diretório
* `is_executable($path);` // Retorna se o caminho é executável
* `is_file($path);` // Retorna se o caminho existe e é um arquivo comum
* `is_link($path);` // Retorna se o caminho existe e é um link simbólico
* `is_readable($path);` // Retorna se o caminho existe e se pode ser lido
* `is_writable($path);` // Retorna se o caminho existe e se pode ser gravado
* `bool is_uploaded_file ( string $filename )`
* `bool file_exists ( string $filename )` - Verifica se o arquivo ou o diretório existe.
* `void clearstatcache ([ bool $clear_realpath_cache = false [, string $filename ]] )`


#### Links


* `bool link ( string $target, string $link )` - Cria um hardlink.
* `bool symlink ( string $target, string $link )` - Cria um link simbólico para o objeto existente com o nome especificado para o link.
* `string readlink ( string $path )` - Retorna o objeto referente ao link simbólico.


* `float disk_free_space ( string $directory )`
* `bool move_uploaded_file ( string $filename, string $destination )`
* `int fseek ( resource $handle, int $offset [, int $whence] )`
   * `SEEK_SET` (inicia no começo do arquivo)
   * `SEEK_CUR` (inicia na posição atual)
   * `SEEK_END` (inicia no final do arquivo)
* `int ftell ( resource $handle )` - retorna resultados indefinidos quando o stream for apenas para acréscimo (aberta com a opção "a").
* `bool ftruncate ( resource $handle, int $size )`
* `array fgetcsv ( resource $handle [, int $length [, string $delimiter [, string $enclosure]]] )`
* `int fputcsv ( resource $handle, array $fields [, string $delimiter [, string $enclosure]] )`
* `int readfile ( string $filename [, bool $use_include_path [, resource $context]] )` - Retorna um arquivo.
* `int fpassthru ( resource $handle )` - Retorna todos os dados remanescentes em um ponteiro de arquivo
* `array file ( string $filename [, int $flags [, resource $context]] )`
* `string implode ( string $glue, array $pieces )`
* `string basename ( string $path [, string $suffix] )`
* `string realpath ( string $path )` - Retorna o caminho absoluto de forma canônica.
* `bool chdir ( string $directory )`
* `string getcwd ( void )`
* `bool unlink ( string $filename [, resource $context] )`
* `bool rename ( string $oldname, string $newname [, resource $context] )` - Tenta renomear um nome antigo para um novo nome.
* `bool rmdir ( string $dirname [, resource $context] )` - Tenta remover um diretório. O diretório precisa estar vazio e as permissões relevantes devem permitir isso.
* `bool mkdir ( string $pathname [, int $mode [, bool $recursive [, resource $context]]] )`
* `string readdir ( resource $dir_handle )` - Lê os dados de um manipulador de diretórios.
* `array scandir ( string $directory [, int $sorting_order [, resource $context]] )` - Retorna um array de arquivos e diretórios com base no diretório indicado.
* `int filectime (string filename)` / `int filemtime (string filename)` - "Last changed time" (data da última alteração) é diferente de "last modified time" (data da última modificação). A data da última alteração se refere as mudanças nos dados do inode do arquivo, incluindo mudanças em permissões, proprietário, grupo e outras informações específicas de inodes. Já a data da última modificação se refere as alterações no conteúdo do arquivo (mais especificamente no seu tamanho em bytes).
* `int fileperms (string filename)`
* `string tempnam ( string $dir , string $prefix )`


* * *

## Streams


* É com eles que o PHP faz a manipulação de recursos de rede
* Sempre que você abre um arquivo, o PHP abre um stream em segundo plano


* * *

### Tipos


* fornecem acesso a certos tipos de recursos stream (embutidos no PHP)
   * `php.*` — entrada e saída padrão do PHP
   * `file` — acesso padrão a arquivos
   * `http` — acesso a recursos remotos via HTTP
   * `ftp` — acesso a recursos remotos via FTP
   * `compress.zlib` — acesso a streams de dados comprimidos usando a biblioteca de compressão zlib.
* stream filters - extensões que podem ser "instaladas" por cima de uma existente para formar cadeias de filtros que agem conjuntamente em um stream de dados
   * `string.rot13` — codifica o stream de dados usando o algoritmo ROT-13
   * `string.toupper` — converte strings para maiúsculas
   * `string.tolower` — converte strings para minúsculas
   * `string.strip_tags` — remove tags XML de um stream
   * `convert.*` — uma família de filtros que converte a partir de, e para, codificação base64
   * `mcrypt.*` — uma família de filtros que criptografa e descriptografa dados de acordo com múltiplos algoritmos
   * `zlib.*` — uma família de filtros que comprimem e descomprimem dados usando a biblioteca de compressão zlib


* * *

### Componentes


* invólucro de arquivos (file wrapper)
* um ou mais pipelines
* um contexto opcional
* metadados relacionados ao stream
* Funções
   * `array stream_get_meta_data ( resource $stream )`
   * `resource stream_context_create ([ array $options [, array $params ]] )`


* * *

### Funções de Stream {#funcoes_de_stream}


* `resource stream_socket_server ( string $local_socket [, int &$errno [, string &$errstr [, int $flags [, resource $context]]]] )`
* `array stream_get_transports ( void )`
* `resource stream_socket_accept ( resource $server_socket [, float $timeout [, string &$peername]] )`
* `array stream_get_wrappers ( void )`
* `bool stream_wrapper_register ( string $protocol, string $classname )`
* `resource stream_socket_client ( string $remote_socket [, int &$errno [, string &$errstr [, float $timeout [, int $flags [, resource $context]]]]] )`
* `string stream_socket_get_name ( resource $handle, bool $want_peer )`
* `bool stream_filter_register ( string $filtername, string $classname )`
* `resource stream_filter_prepend ( resource $stream, string $filtername [, int $read_write [, mixed $params]] )`
* `resource stream_filter_append ( resource $stream, string $filtername [, int $read_write [, mixed $params]] )`
* `int stream_select ( array &$read , array &$write , array &$except , int $tv_sec [, int $tv_usec = 0 ] )`


* * *

### Sockets

{% highlight php5 linenos %}
<?php
$fp = fsockopen("example.preinheimer.com", 80, $errno, $errstr, 30)
{% endhighlight %}


* * *

## Contextos

<http://php.net/manual/pt_BR/context.php>

* `resource stream_context_create ([ array $options [, array $params ]] )`
* `bool stream_context_set_option ( resource $stream_or_context , string $wrapper , string $option , mixed $value )`
* `bool stream_context_set_option ( resource $stream_or_context , array $options )`
* `bool stream_context_set_params ( resource $stream_or_context , array $params )`

{% highlight php5 linenos %}
<?php
$opts = array(
  'http'=>array(
    'method'=>"GET",
    'header'=>"Accept-language: en\r\n" .
              "Cookie: foo=bar\r\n"
  )
);

$context = stream_context_create($opts);

/* Sends an http request to www.example.com
   with additional headers shown above */
$fp = fopen('http://www.example.com', 'r', false, $context);
fpassthru($fp);
fclose($fp);
{% endhighlight %}
