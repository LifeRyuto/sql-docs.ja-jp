---
title: Sqlsetdescfield による |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQLSetDescField function
ms.assetid: de4bed15-15be-4825-994c-1046255e725a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: f65c26e1c6b9588b770acf1a66409dfde8ea1072
ms.sourcegitcommit: 334cae1925fa5ac6c140e0b2c38c844c477e3ffb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/13/2018
ms.locfileid: "53362126"
---
# <a name="sqlsetdescfield"></a>SQLSetDescField
  Sqlsetdescfield によるは、テーブル値パラメーターおよびテーブル値パラメーター列の記述子フィールドを設定するのには使用できます。 使用可能なフィールドの詳細については、[テーブル値パラメーターの記述子フィールド](../native-client-odbc-table-valued-parameters/table-valued-parameter-descriptor-fields.md)と[テーブル値パラメーターの構成要素の列の記述子フィールド](../native-client-odbc-table-valued-parameters/descriptor-fields-for-table-valued-parameter-constituent-columns.md)を参照してください。  
  
## <a name="remarks"></a>コメント  
 テーブル値パラメーター列は、記述子のヘッダー フィールド SQL_SOPT_SS_PARAM_FOCUS に、SQL_DESC_TYPE が SQL_SS_TABLE に設定されているレコードの序数が設定される場合のみ使用できます。 SQL_SOPT_SS_PARAM_FOCUS の詳細については、[SQLSetStmtAttr](sqlsetstmtattr.md)を参照してください。  
  
 テーブル値パラメーターのないパラメーターの序数に SQL_SOPT_SS_PARAM_FOCUS を設定しようとしましたが、SQLSetStmtAttr が、SQL_ERROR を返し、sqlstate 診断レコードが作成された場合は、HY024 とメッセージ「無効な属性値」を = します。 SQL_SOPT_SS_PARAM_FOCUS は、SQL_ERROR が返されたときに変更されません。  
  
 SQL_SOPT_SS_PARAM_FOCUS に 0 を設定すると、パラメーターの記述子レコードへのアクセスが復元されます。  
  
 テーブル値パラメーターの詳細については、[テーブル値パラメーター &#40;ODBC&#41;](../native-client-odbc-table-valued-parameters/table-valued-parameters-odbc.md)を参照してください。  
  
## <a name="sqlsetdescfield-support-for-enhanced-date-and-time-features"></a>SQLSetDescField による機能強化された日付と時刻のサポート  
 ODBC では、日付と時刻の機能が強化されました。 新しい日付/時刻型の指定された記述子フィールドについては、[パラメーターと結果のメタデータ](../native-client-odbc-date-time/metadata-parameter-and-result.md)を参照してください。  
  
 詳細については、[日付と時刻の強化&#40;ODBC&#41;](../native-client-odbc-date-time/date-and-time-improvements-odbc.md)を参照してください。  
  
## <a name="sqlsetdescfield-support-for-large-clr-udts"></a>SQLSetDescField による大きな CLR UDT のサポート  
 Sqlsetdescfield による大きなの CLR ユーザー定義型 (Udt) をサポートしています。 詳細については、[Large CLR User-Defined 型&#40;ODBC&#41;](../native-client/odbc/large-clr-user-defined-types-odbc.md)を参照してください。  
  
## <a name="sqlsetdescfield-support-for-sparse-columns"></a>SQLSetDescField によるスパース列のサポート  
 SQLSetDecField sql_sopt_ss_name_scope を SQL_SS_NAME_SCOPE_EXTENDED および SQL_SS_NAME_SCOPE_SPARSE_COLUMN_SET 値にアプリケーション パラメーター記述子 (APD) を使用できます。  
  
 詳細については、[スパース列のサポート&#40;ODBC&#41;](../native-client/odbc/sparse-columns-support-odbc.md)を参照してください。  
  
## <a name="see-also"></a>参照  
 [Sqlsetdescfield による](https://go.microsoft.com/fwlink/?LinkId=80705)   
 [ODBC API 実装の詳細](odbc-api-implementation-details.md)  
  
  
