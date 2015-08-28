---
layout: page
title: "Banco de dados"
description: ""
---
{% include JB/setup %}

{% include menu/databases.md %}


* * *

## Fatos

* Versões recentes do PHP  não (mais) vêm acompanhadas com a extensão do MySQL embutida.
* Agora há duas versões de extensões do MySQL disponíveis, MySQL e MySQLi
* A extensão MySQLi torna algumas das mais recentes funcionalidades do MySQL disponíveis, como declarações preparadas


* * *

## Analisando Consultas


* `EXPLAIN` TUDO!
* `EXPLAIN SELECT * FROM 07_amazon_monitor_rank_results WHERE asin = '0672324547'`;


* * *

## Declarações preparadas (Prepared Statements)

* Permite a você aumentar a velocidade de consultas repetitivas, e isolar dados do comando
* Primeiro prepara-se a declaração, então vincula-se parâmetros a ela, e então a executa
* <http://php.net/manual/pt_BR/mysqli.prepare.php>
* Parâmetros vinculados (Bound Parameters)
* Um parâmetro vinculado permite guardar uma consulta no servidor MySQL, com apenas os dados iterativos sendo repetidamente enviados ao servidor, e integrados na consulta para execução.
* Resultados vinculados (Bound Results)
* Um resultado vinculado permite utilizar arrays indexados ou associativos para obter valores dos conjuntos de resultado, para isso, vincula-se variáveis PHP aos campos obtidos correspondentes, e então utiliza-se essas variáveis como for necessário
* Depois que uma consulta já foi preparada e executada, é possível vincular variáveis aos campos obtidos, utilizando $stmt->bind_result.

{% highlight php5 linenos %}
<?php
boolean mysqli_stmt_bind_param (mysqli_stmt stmt, string types, mixed &var1 [, mixed &varN)
class mysqli_stmt {
    boolean bind_param (string types, mixed &var1 [, mixed &varN])
}

boolean mysqli_stmt_bind_result (mysqli_stmt stmt, mixed &var1 [, mixed &varN])

class mysqli_stmt {
    boolean bind_result (mixed &var1 [, mixed &varN])
}
{% endhighlight %}

* * *

## Mysqli


{% highlight php5 linenos %}
<?php
$link = mysqli_connect("localhost", "u", "p", "ex");
$city = "Montreal";
$stmt = mysqli_stmt_init($link);
if ($stmt = mysqli_stmt_prepare ($stmt, "SELECT Province FROM City WHERE Name=?"))
{
mysqli_stmt_bind_param($stmt, "s", $city);
mysqli_stmt_execute($stmt);
mysqli_stmt_bind_result($stmt, $province);
mysqli_stmt_fetch($stmt);
printf("%s is in district %s\n", $city, $province);
mysqli_stmt_close($stmt);
}
mysqli_close($link);
{% endhighlight %}


* * *

## Transações (Transactions)

Permite juntar (merge) diversas consultas em uma operação atômica, ou TODAS executam com sucesso, ou nenhuma executara

{% highlight mysql linenos %}
BEGIN TRANSACTION #name;
 ... queries here
COMMIT;
{% endhighlight %}

* * *

## PDO


* [PHP Data Objects](http://php.net/pdo)
* Método consistente orientado a objetos para interagir com diversos banco de dados
* Driver PDO especifico do banco de dados deve ser instalado

{% highlight php5 linenos %}
<?php
$pdoConnection = new PDO('mysql:host=localhost;dbname=example', USERNAME, PASSWORD);
foreach ($pdoConnection->query("SELECT * FROM users") AS $user) { echo $user['id']; }
{% endhighlight %}


Declarações Preparadas


{% highlight php5 linenos %}
<?php
$query = "SELECT * FROM posts WHERE topicID = :tid AND poster = :userid";
$statement = $pdoConnection->prepare($query, array(PDO::ATTR_CURSOR, PDO::CURSOR_FWDONLY));
$statement->execute(array(':tid' => 100, ':userid' => 12));
$userAPosts = $statement->fetchAll();
$statement->execute(array(':tid' => 100, ':userid' => 13));
$userBPosts = $statement->fetchAll();
{% endhighlight %}

fechando conexão

{% highlight php5 linenos %}
<?php
$pdoConnection = null; // 
{% endhighlight %}

{% highlight php5 linenos %}
<?php
PDOStatement->nextRowset()
{% endhighlight %}

`array PDO::errorInfo ( void )`
* 0 - Código de erro SQLSTATE (um identificador de cinco caracteres alfanuméricos definido pelo padrão do ANSI SQL)
* 1 - Código de erro especifico indicado pelo driver.
* 2 - Mensagem especifica de erro indicada pelo driver.



* * *

## SQLite


* é um banco de dados, sem o banco de dados
* em vez de usar um programa separado para persistentemente manter o banco de dados, o SQLite requisita de bibliotecas C que compreende o banco de dados para que este seja incluído em qualquer programa que deseje utiliza-lo
* foi incluído na versão 5 do PHP por padrão
* É rápido, grátis, e possui uma boa licença
* Com exceção de não precisar conectar em um servidor ou processo remoto, o SQLite não é diferente dos outros sistemas de banco de dados
* categoriza o dado em textual e numérico