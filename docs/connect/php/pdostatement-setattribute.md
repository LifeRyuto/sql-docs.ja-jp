---
title: Pdostatement::setattribute |Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 329d9b5e-1c5d-40b0-9127-1051d0646fc7
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3ec2ed7275c3580554c385940c5cef134244ae35
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744342"
---
# <a name="pdostatementsetattribute"></a>PDOStatement::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済み PDO 属性またはカスタム ドライバー属性のいずれかの属性値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDOStatement::setAttribute ($attribute, $value );  
```  
  
#### <a name="parameters"></a>パラメーター  
$*attribute*: PDO::ATTR_* または PDO::SQLSRV_ATTR_\* 定数のいずれかの整数。 使用可能な属性の一覧については、「解説」セクションを参照してください。  
  
$*value*: 指定された $*attribute* に設定される (複合) 値。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE です。  
  
## <a name="remarks"></a>Remarks  
次の表に、使用可能な属性の一覧を示します。  
  
|attribute|値|[説明]|  
|-------------|----------|---------------|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|PHP メモリの制限に 1。|クライアント側カーソルの結果セットを保持するバッファーのサイズを設定します。<br /><br />既定値は 10,240 KB (10 MB) です。<br /><br />クライアント側カーソルの詳細については、「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|0 ~ 4 の (範囲) の整数|フェッチされる money 値を書式設定時に、小数点以下桁数の数を指定します。<br /><br />任意の負の整数値または値が 4 よりも詳細は無視されます。<br /><br />このオプションは、PDO::SQLSRV_ATTR_FORMAT_DECIMALS が true の場合にのみ機能します。<br /><br />このオプションは、接続レベルでも設定できます。 そうである場合、このオプションは接続レベルのオプションをオーバーライドします。<br /><br />詳細については、次を参照してください。 [10 進数値文字列の書式設定および通貨値 (PDO_SQLSRV ドライバー)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)します。|
|PDO::SQLSRV_ATTR_ENCODING|Integer<br /><br />PDO::SQLSRV_ENCODING_UTF8 (既定)<br /><br />PDO::SQLSRV_ENCODING_SYSTEM<br /><br />PDO::SQLSRV_ENCODING_BINARY|ドライバーがサーバーとの通信に使用する文字セット エンコーディングを設定します。|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|true または false|日付と時刻の型として取得するかどうかを指定します[PHP DateTime](http://php.net/manual/en/class.datetime.php)オブジェクト。 False のままにした場合、既定の動作では、文字列として返すことです。<br /><br />このオプションは、接続レベルでも設定できます。 そうである場合、このオプションは接続レベルのオプションをオーバーライドします。<br /><br />詳細については、次を参照してください。[方法: 取得日付と時刻型として PHP DateTime オブジェクトを使用して、PDO_SQLSRV ドライバー](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)します。|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|true または false|(ビット、整数、smallint、tinyint、float または real) の数値の SQL 型の列からの数値のフェッチを処理します。<br /><br />接続オプション フラグ ATTR_STRINGIFY_FETCHES が on の場合、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がある場合でも、戻り値では文字列が使用します。<br /><br />バインド列で返される PDO 型 PDO_PARAM_INT が SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がオフの場合でも、整数型の列からの戻り値は int が。|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|true または false|該当する場合に、10 進数値の文字列に先頭のゼロを追加するかどうかを指定します。 場合、このオプションを設定では、PDO::SQLSRV_ATTR_DECIMAL_PLACES の money 型の書式設定オプションを有効します。 False のままにした場合は、正確な有効桁数を返すと、先頭の値が 1 未満のゼロを省略すると、既定の動作が使用されます。<br /><br />このオプションは、接続レベルでも設定できます。 そうである場合、このオプションは接続レベルのオプションをオーバーライドします。<br /><br />詳細については、次を参照してください。 [10 進数値文字列の書式設定および通貨値 (PDO_SQLSRV ドライバー)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)します。| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|Integer|クエリのタイムアウト (秒単位) を設定します。<br /><br />既定で、ドライバーは、結果を無制限に待機します。 負の数値は許可できません。<br /><br />0 は、タイムアウトがないことを示します。|  
  
## <a name="example"></a>例  
  
```  
<?php  
$database = "AdventureWorks";  
$server = "(local)";  
$conn = new PDO( "sqlsrv:server=$server ; Database = $database", "", "", array('MultipleActiveResultSets'=>false )  );  
  
$stmt = $conn->prepare('SELECT * FROM Person.ContactType');  
  
echo $stmt->getAttribute( constant( "PDO::ATTR_CURSOR" ) );  
  
echo "\n";  
  
$stmt->setAttribute(PDO::SQLSRV_ATTR_QUERY_TIMEOUT, 2);  
echo $stmt->getAttribute( constant( "PDO::SQLSRV_ATTR_QUERY_TIMEOUT" ) );  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDOStatement クラス](../../connect/php/pdostatement-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
