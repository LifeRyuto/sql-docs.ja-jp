---
title: ステートメントの実行の PDO_SQLSRV ドライバーの準備のステートメントを直接 |Microsoft Docs
ms.custom: ''
ms.date: 03/26/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 05544ca6-1e07-486c-bf03-e8c2c25b3024
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 96a03a678152c523cdb16b77834863ff920586c8
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801458"
---
# <a name="direct-statement-execution-and-prepared-statement-execution-in-the-pdosqlsrv-driver"></a>Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行)
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

このトピックでは、PDO::SQLSRV_ATTR_DIRECT_QUERY 属性を使用して、準備されたステートメントの実行である既定ではなく、直接のステートメントの実行を指定する方法について説明します。 準備されたステートメントを使用すると、2 回以上のパラメーターのバインドを使用してステートメントを実行する場合にパフォーマンスを向上させるが発生することができます。  
  
## <a name="remarks"></a>Remarks  
送信する場合、[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントでは、ドライバーによってステートメントの準備なしでサーバーに直接、pdo::sqlsrv_attr_direct_query 属性を設定する[pdo::setattribute](../../connect/php/pdo-setattribute.md) (または、ドライバーのオプションに渡されます[:: _ _Construct](../../connect/php/pdo-construct.md)) を呼び出すとまたは[pdo::prepare](../../connect/php/pdo-prepare.md)します。 既定では pdo::sqlsrv_attr_direct_query の値は False です (準備ステートメントの実行を使用します)。  
  
使用する場合[pdo::query](../../connect/php/pdo-query.md)、直接実行する場合があります。 呼び出しの前に[pdo::query](../../connect/php/pdo-query.md)、呼び出す[pdo::setattribute](../../connect/php/pdo-setattribute.md) pdo::sqlsrv_attr_direct_query を True に設定します。  呼び出しごとに[pdo::query](../../connect/php/pdo-query.md) pdo::sqlsrv_attr_direct_query のさまざまな設定で実行できます。  
  
使用する場合[pdo::prepare](../../connect/php/pdo-prepare.md)と[pdostatement::execute](../../connect/php/pdostatement-execute.md)複数回のクエリを実行する準備ステートメントの実行のバインドされたパラメーターを使用する繰り返しのクエリの実行を最適化します。  このような状況で呼び出す[pdo::prepare](../../connect/php/pdo-prepare.md)で pdo::sqlsrv_attr_direct_query のドライバーのオプション配列パラメーターに False に設定します。 必要に応じて、pdo::sqlsrv_attr_direct_query は False に設定と準備されたステートメントを実行できます。  
  
呼び出した後[pdo::prepare](../../connect/php/pdo-prepare.md)、準備されたクエリを実行するときに pdo::sqlsrv_attr_direct_query の値を変更することはできません。  
  
クエリは、前のクエリで設定されたコンテキストを必要とする場合は、pdo::sqlsrv_attr_direct_query の設定を True に、クエリを実行します。 たとえば場合は、クエリで一時テーブルを使用すると、pdo::sqlsrv_attr_direct_query を True に設定する必要があります。  
  
次の例では、前のステートメントからのコンテキストが必要な場合は、pdo::sqlsrv_attr_direct_query を True に設定する必要がありますを示します。 このサンプルは、クエリが直接実行されたときに、プログラム内の後続のステートメントでのみ使用できる一時テーブルを使用します。  
  
> [!NOTE]
> クエリは、ストアド プロシージャを呼び出すし、一時テーブルを使用して、このストアド プロシージャで使用する場合[:exec](../../connect/php/pdo-exec.md)代わりにします。

```  
<?php  
   $conn = new PDO('sqlsrv:Server=(local)', '', '');  
   $conn->setAttribute(constant('PDO::SQLSRV_ATTR_DIRECT_QUERY'), true);  
  
   $stmt1 = $conn->query("DROP TABLE #php_test_table");  
  
   $stmt2 = $conn->query("CREATE TABLE #php_test_table ([c1_int] int, [c2_int] int)");  
  
   $v1 = 1;  
   $v2 = 2;  
  
   $stmt3 = $conn->prepare("INSERT INTO #php_test_table (c1_int, c2_int) VALUES (:var1, :var2)");  
  
   if ($stmt3) {  
      $stmt3->bindValue(1, $v1);  
      $stmt3->bindValue(2, $v2);  
  
      if ($stmt3->execute())  
         echo "Execution succeeded\n";       
      else  
         echo "Execution failed\n";  
   }  
   else  
      var_dump($conn->errorInfo());  
  
   $stmt4 = $conn->query("DROP TABLE #php_test_table");  
?>  
```  
  
## <a name="see-also"></a>参照  
[For PHP for SQL Server のプログラミング、Microsoft ドライバーのガイド](../../connect/php/programming-guide-for-php-sql-driver.md)
  
