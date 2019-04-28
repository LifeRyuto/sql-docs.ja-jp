---
title: クライアントにサーバーから変換 |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: ''
ms.topic: reference
helpviewer_keywords:
- conversions [OLE DB], server to client
ms.assetid: 676fdf24-fb72-4ea0-a8d2-2b197da3c83f
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4f5df8d27f39918cb8ddac4dd46dd8b3ca4449c5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62704465"
---
# <a name="conversions-performed-from-server-to-client"></a>サーバーからクライアントへの変換
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  このトピックでは、[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] (以降) と、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client OLE DB で作成されたクライアント アプリケーションとの間で実行される日付または時刻の変換について説明します。  
  
## <a name="conversions"></a>コンバージョン  
 次の表では、クライアントに返される型とバインドの型との間の変換について説明しています。 Icommandwithparameters::setparameterinfo が呼び出され、型がで指定された場合、出力パラメーターの*して*サーバーによって実行される暗黙的な変換をサーバー上の実際の型と一致しません、と、クライアントに返される型の icommandwithparameters::setparameterinfo を通じて指定された型が一致します。 これは、サーバーの変換の規則がこのトピックで説明されているものとは異なると、予期しない変換結果につながることができます。 たとえば、既定の日付を指定する必要がある場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では 1899-12-30 ではなく 1900-1-1 が使用されます。  
  
|-><br /><br /> From|[DATE]|DBDATE|DBTIME|DBTIME2|DBTIMESTAMP|DBTIMESTAMPOFFSET|FILETIME|BYTES|VARIANT|SSVARIANT|BSTR|STR|WSTR|  
|----------------------|----------|------------|------------|-------------|-----------------|-----------------------|--------------|-----------|-------------|---------------|----------|---------|----------|  
|date|1,7|[OK]|-|-|1|1,3|1,7|-|[OK] \(VT_BSTR)|[OK]|[OK]|4|4|  
|Time|5,6,7|-|9|[OK]|6|3,6|5,6|-|[OK] \(VT_BSTR)|[OK]|[OK]|4|4|  
|Smalldatetime|7|8|9,10|10|[OK]|3|7|-|7 (VT_DATE)|[OK]|[OK]|4|4|  
|DATETIME|5,7|8|9,10|10|[OK]|3|7|-|7 (VT_DATE)|[OK]|[OK]|4|4|  
|Datetime2|5,7|8|9,10|10|7|3|5,7|-|[OK] \(VT_BSTR)|[OK]|[OK]|4|4|  
|Datetimeoffset|5,7,11|8,11|9,10,11|10,11|7,11|[OK]|5,7,11|-|[OK] \(VT_BSTR)|[OK]|[OK]|4|4|  
|Char、Varchar、<br /><br /> Nchar、Nvarchar|7, 13|12|12,9|12|12|12|7,13|なし|なし|なし|なし|なし|なし|  
|Sql_variant<br /><br /> (datetime)|7|8|9,10|10|[OK]|3|7|-|7 (VT_DATE)|[OK]|[OK]|4|4|  
|Sql_variant<br /><br /> (smalldatetime)|7|8|9,10|10|[OK]|3|7|-|7 (VT_DATE)|[OK]|[OK]|4|4|  
|Sql_variant<br /><br /> (date)|1,7|[OK]|2|2|1|1,3|1,7|-|OK (VT_BSTR)|[OK]|[OK]|4|4|  
|Sql_variant<br /><br /> (time)|5,6,7|2|6|[OK]|6|3,6|5,6|-|OK (VT_BSTR)|[OK]|[OK]|4|4|  
|Sql_variant<br /><br /> (datetime2)|5,7|8|9,10|10|[OK]|3|5,7|-|OK (VT_BSTR)|[OK]|[OK]|4|4|  
|Sql_variant<br /><br /> (datetimeoffset)|5,7,11|8,11|9,10,11|10,11|7,11|[OK]|5,7,11|-|OK (VT_BSTR)|[OK]|[OK]|4|4|  
  
## <a name="key-to-symbols"></a>記号の説明  
  
|シンボル|説明|  
|------------|-------------|  
|[OK]|変換は必要ありません。|  
|-|変換はサポートされていません。 Iaccessor::createaccessor が呼び出されたときに、バインドが検証されると、DBBINDSTATUS_UPSUPPORTEDCONVERSION がで返されます*rgStatus*します。 アクセサー検証が遅延する場合は、DBSTATUS_E_BADACCESSOR が設定されます。|  
|1|時刻フィールドに 0 が設定されます。|  
|2|DBSTATUS_E_CANTCONVERTVALUE が設定されます。|  
|3|タイムゾーンは 0 に設定されます。|  
|4|クライアント バッファーのサイズが十分でない場合、DBSTATUS_S_TRUNCATED が設定されます。 サーバーの型に秒の小数部が含まれている場合、結果文字列の桁数はサーバーの型の小数点以下桁数と完全に一致します。|  
|5|秒または秒の小数部の切り捨ては無視されます。|  
|6|日付は現在の日付に設定されます。ただし、変換元が時間の文字列リテラルで、変換先が DBTYPE_DATE の場合は別です。 この場合、1899-12-30 が使用されます。|  
|7|値がオーバーフローする場合は、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
|8|時刻フィールドは無視されます。|  
|9|秒の小数部のフィールドは無視されます。|  
|10|日付部分は無視されます。|  
|11|時刻はクライアントのタイム ゾーンに変換されます。 この変換中にエラーが発生した場合、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
|12|文字列は ISO リテラルとして解析され、対象の型に変換されます。 これが失敗すると、文字列は OLE 日付リテラル (時刻要素も含む) として解析され、OLE Date (DBTYPE_DATE) から対象の型に変換されます。 文字列は、ISO 形式の解析を成功させるために許可された対象の型のリテラルの構文に準拠している必要があります。 OLE での解析を成功させるには、文字列は OLE で認識される構文に準拠している必要があります。 文字列を解析できない場合は、DBSTATUS_E_CANTCONVERTVALUE が設定されます。 任意の部分の値が範囲外の場合は、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
|13|文字列は ISO リテラルとして解析され、対象の型に変換されます。 これが失敗すると、文字列は OLE 日付リテラル (時刻要素も含む) として解析され、OLE Date (DBTYPE_DATE) から対象の型に変換されます。 文字列は datetime リテラルの構文に準拠している必要があります。ただし、変換先が DBTYPE_DATE または DBTYPE_DBTIMESTAMP の場合は別です。 この場合、ISO 形式の解析を成功させるために、datetime リテラルまたは時刻リテラルが許容されています。 OLE での解析を成功させるには、文字列は OLE で認識される構文に準拠している必要があります。 文字列を解析できない場合は、DBSTATUS_E_CANTCONVERTVALUE が設定されます。 任意の部分の値が範囲外の場合は、DBSTATUS_E_DATAOVERFLOW が設定されます。|  
  
## <a name="see-also"></a>参照  
 [バインドと変換 &#40;OLE DB&#41;](../../relational-databases/native-client-ole-db-date-time/conversions-ole-db.md)  
  
  
