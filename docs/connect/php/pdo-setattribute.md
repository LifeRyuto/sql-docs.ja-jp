---
title: Pdo::setattribute |Microsoft Docs
ms.custom: ''
ms.date: 02/11/2019
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 56f9ee96-e1d2-46cc-b137-38f06a251863
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b0109eef02bc3649617b4f1f414406665c16ba9
ms.sourcegitcommit: 958cffe9288cfe281280544b763c542ca4025684
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 02/23/2019
ms.locfileid: "56744652"
---
# <a name="pdosetattribute"></a>PDO::setAttribute
[!INCLUDE[Driver_PHP_Download](../../includes/driver_php_download.md)]

定義済み PDO 属性またはカスタム ドライバー属性を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
bool PDO::setAttribute ( $attribute, $value );  
```  
  
#### <a name="parameters"></a>パラメーター  
*$attribute*: 設定する属性。 サポートされる属性の一覧については、「解説」セクションを参照してください。  
  
*$value*: 値 (混在型)。  
  
## <a name="return-value"></a>戻り値  
成功した場合は TRUE、それ以外の場合は FALSE を返します。  
  
## <a name="remarks"></a>Remarks  
  
|属性|処理を行った機能|サポートされている値|[説明]|  
|-------------|----------------|--------------------|---------------|  
|PDO::ATTR_CASE|PDO|PDO::CASE_LOWER<br /><br />PDO::CASE_NATURAL<br /><br />PDO::CASE_UPPER|列名の大文字/小文字を指定します。<br /><br />PDO::CASE_LOWER は列名を小文字にします。<br /><br />PDO::CASE_NATURAL (既定値) は、データベースにより返されたとおりの列名を表示します。<br /><br />PDO::CASE_UPPER は列名を大文字にします。<br /><br />この属性は PDO::setAttribute を使用して設定できます。|  
|PDO::ATTR_DEFAULT_FETCH_MODE|PDO|PDO のドキュメントを参照してください。|PDO のドキュメントを参照してください。|  
|PDO::ATTR_ERRMODE|PDO|PDO::ERRMODE_SILENT<br /><br />PDO::ERRMODE_WARNING<br /><br />PDO::ERRMODE_EXCEPTION|ドライバーがエラーを報告する方法を指定します。<br /><br />PDO::ERRMODE_SILENT (既定値) は、エラー コードと情報を設定します。<br /><br />PDO::ERRMODE_WARNING は、E_WARNING を生成します。<br /><br />PDO::ERRMODE_EXCEPTION は、例外をスローします。<br /><br />この属性は PDO::setAttribute を使用して設定できます。|  
|PDO::ATTR_ORACLE_NULLS|PDO|PDO のドキュメントを参照してください。|null を返す方法を指定します。<br /><br />PDO::NULL_NATURAL は変換を行いません。<br /><br />PDO::NULL_EMPTY_STRING は空の文字列を null に変換します。<br /><br />PDO::NULL_TO_STRING は null を空の文字列に変換します。|  
|PDO::ATTR_STATEMENT_CLASS|PDO|PDO のドキュメントを参照してください。|PDOStatement から誘導されたユーザー指定のステートメント クラスを設定します。<br /><br />`array(string classname, array(mixed constructor_args))`を必要とします。<br /><br />詳細については、PDO のドキュメントを参照してください。|  
|PDO::ATTR_STRINGIFY_FETCHES|PDO|true または false|データの取得時に数値を文字列に変換します。|  
|PDO::SQLSRV_ATTR_CLIENT_BUFFER_MAX_KB_SIZE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PHP メモリの制限に 1。|クライアント側カーソルを使用するときに結果セットを保持するバッファーのサイズを設定します。<br /><br />デフォルトは 10240 KB ですがない場合、php.ini ファイルで指定します。<br /><br />ゼロおよび負の数値は許可できません。<br /><br />クライアント側カーソルを作成するクエリの詳細については、「[カーソルの種類 &#40;PDO_SQLSRV ドライバー&#41;](../../connect/php/cursor-types-pdo-sqlsrv-driver.md)」を参照してください。|  
|PDO::SQLSRV_ATTR_DECIMAL_PLACES|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|0 ~ 4 の (範囲) の整数|フェッチされる money 値を書式設定時に、小数点以下桁数の数を指定します。<br /><br />任意の負の整数値または値が 4 よりも詳細は無視されます。<br /><br />このオプションは、PDO::SQLSRV_ATTR_FORMAT_DECIMALS が true の場合にのみ機能します。<br /><br />このオプションをステートメント レベルの設定もできます。 そうである場合、ステートメント レベルのオプションはこの 1 つをオーバーライドします。<br /><br />詳細については、次を参照してください。 [10 進数値文字列の書式設定および通貨値 (PDO_SQLSRV ドライバー)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)します。|
|PDO::SQLSRV_ATTR_DIRECT_QUERY|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|クエリの直接実行または準備された実行を指定します。 詳細については、「 [Direct Statement Execution and Prepared Statement Execution in the PDO_SQLSRV Driver](../../connect/php/direct-statement-execution-prepared-statement-execution-pdo-sqlsrv-driver.md)」 (PDO_SQLSRV ドライバーでの直接ステートメント実行と準備されたステートメントの実行) を参照してください。|  
|PDO::SQLSRV_ATTR_ENCODING|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|PDO::SQLSRV_ENCODING_UTF8<br /><br />PDO::SQLSRV_ENCODING_SYSTEM.|ドライバーがサーバーとの通信に使用する文字セット エンコーディングを設定します。<br /><br />PDO::SQLSRV_ENCODING_BINARY はサポートされていません。<br /><br />既定値は PDO::SQLSRV_ENCODING_UTF8 です。|  
|PDO::SQLSRV_ATTR_FETCHES_DATETIME_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|日付と時刻の型として取得するかどうかを指定します[PHP DateTime](http://php.net/manual/en/class.datetime.php)オブジェクト。 False のままにした場合、既定の動作では、文字列として返すことです。<br /><br />このオプションをステートメント レベルの設定もできます。 そうである場合、ステートメント レベルのオプションはこの 1 つをオーバーライドします。<br /><br />詳細については、次を参照してください。[方法: 取得日付と時刻型として PHP DateTime オブジェクトを使用して、PDO_SQLSRV ドライバー](../../connect/php/how-to-retrieve-datetime-objects-using-pdo-sqlsrv-driver.md)します。|  
|PDO::SQLSRV_ATTR_FETCHES_NUMERIC_TYPE|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|(ビット、整数、smallint、tinyint、float または real) の数値の SQL 型の列からの数値のフェッチを処理します。<br /><br />接続オプション フラグ ATTR_STRINGIFY_FETCHES が on の場合、SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がある場合でも、戻り値では文字列が使用します。<br /><br />バインド列で返される PDO 型 PDO_PARAM_INT が SQLSRV_ATTR_FETCHES_NUMERIC_TYPE がオフの場合でも、整数型の列からの戻り値は int が。|  
|PDO::SQLSRV_ATTR_FORMAT_DECIMALS|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|true または false|該当する場合に、10 進数値の文字列に先頭のゼロを追加するかどうかを指定します。 場合、このオプションを設定では、PDO::SQLSRV_ATTR_DECIMAL_PLACES の money 型の書式設定オプションを有効します。 False のままにした場合は、正確な有効桁数を返すと、先頭の値が 1 未満のゼロを省略すると、既定の動作が使用されます。<br /><br />このオプションをステートメント レベルの設定もできます。 そうである場合、ステートメント レベルのオプションはこの 1 つをオーバーライドします。<br /><br />詳細については、次を参照してください。 [10 進数値文字列の書式設定および通貨値 (PDO_SQLSRV ドライバー)](../../connect/php/formatting-decimals-pdo-sqlsrv-driver.md)します。| 
|PDO::SQLSRV_ATTR_QUERY_TIMEOUT|[!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]|整数 (integer)|クエリのタイムアウト (秒単位) を設定します。<br /><br />既定値は 0 であり、ドライバーは結果をいつまでも待ちます。<br /><br />負の数値は許可できません。|  
  
一部の定義済み属性は PDO で処理されますが、他の属性はドライバーで処理する必要があります。 カスタム属性と接続オプションはすべてドライバーにより処理されます。 サポートされない属性、接続オプション、サポートされない値は PDO::ATTR_ERRMODE の設定に基づいて報告されます。  
  
PDO のサポートは [!INCLUDE[ssDriverPHP](../../includes/ssdriverphp_md.md)]のバージョン 2.0 で追加されました。  
  
## <a name="example"></a>例  
このサンプルは、PDO::ATTR_ERRMODE 属性を設定する方法を示しています。  
  
```  
<?php  
   $database = "AdventureWorks";  
   $conn = new PDO( "sqlsrv:server=(local) ; Database = $database", "", "");  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
  
   $conn->setAttribute( PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION );  
  
   $attributes1 = array( "ERRMODE" );  
   foreach ( $attributes1 as $val ) {  
      echo "PDO::ATTR_$val: ";  
      var_dump ($conn->getAttribute( constant( "PDO::ATTR_$val" ) ));  
   }  
?>  
```  
  
## <a name="see-also"></a>参照  
[PDO クラス](../../connect/php/pdo-class.md)

[PDO](https://php.net/manual/book.pdo.php)  
  
