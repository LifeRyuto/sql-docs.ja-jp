---
title: 暗黙のカーソル変換 (ODBC) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- ODBC cursors, implicit cursor conversions
- implicit cursor conversions
- cursors [ODBC], implicit cursor conversions
ms.assetid: fe29a58d-8448-4512-9ffd-b414784ba338
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: eebbfcefdf5c4c9e2d6ed1409e3c119f598a22d1
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63013600"
---
# <a name="implicit-cursor-conversions-odbc"></a>暗黙のカーソル変換 (ODBC)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../../includes/snac-deprecated.md)]

  アプリケーションでのカーソルの種類を要求できます。 [SQLSetStmtAttr](../../../relational-databases/native-client-odbc-api/sqlsetstmtattr.md) 、要求された型のサーバー カーソルでサポートされていない SQL ステートメントを実行します。 呼び出し**SQLExecute**または**SQLExecDirect** sql_success_with_info と**SQLGetDiagRec**を返します。  
  
```  
szSqlState = "01S02", *pfNativeError = 0,  
szErrorMsg="[Microsoft][SQL Server Native Client] Cursor type changed"  
```  
  
 カーソルの種類は、呼び出すことによって使用されているようになりましたが、アプリケーションが判断できます**SQLGetStmtOption** SQL_CURSOR_TYPE を設定します。 カーソルの種類の変換は、1 つのステートメントにのみ適用されます。 次**SQLExecDirect**または**SQLExecute**行われます元のステートメントのカーソル設定を使用します。  
  
## <a name="see-also"></a>参照  
 [カーソル プログラミングの詳細&#40;ODBC&#41;](../../../relational-databases/native-client-odbc-cursors/programming/cursor-programming-details-odbc.md)  
  
  
