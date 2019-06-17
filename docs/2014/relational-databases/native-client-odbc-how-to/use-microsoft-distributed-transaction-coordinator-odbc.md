---
title: 使用して、Microsoft 分散トランザクション コーディネーター (ODBC) |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- MS DTC, using
ms.assetid: 12a275e1-8c7e-436d-8a4e-b7bee853b35c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 739d87c7a590489a2dd263535356b0b520a4a9b7
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63200228"
---
# <a name="use-microsoft-distributed-transaction-coordinator-odbc"></a>Microsoft 分散トランザクション コーディネーターの使用 (ODBC)
    
### <a name="to-update-two-or-more-sql-servers-by-using-ms-dtc"></a>MS DTC を使用して複数の SQL Server を更新するには  
  
1.  MS DTC の OLE DtcGetTransactionManager 関数を使用して、MS DTC に接続します。 MS DTC の詳細については、Microsoft 分散トランザクション コーディネーターを参照してください。  
  
2.  各 microsoft ずつ SQL DriverConnect を 1 回呼び出します。 SQL Server 接続を確立します。  
  
3.  MS DTC の OLE ITransactionDispenser::BeginTransaction 関数を呼び出して、MS DTC トランザクションを開始し、トランザクションを表すトランザクション オブジェクトを取得します。  
  
4.  MS DTC トランザクションに参加させる ODBC 接続ごとに、[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) を 1 回以上呼び出します。 [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) の 2 番目のパラメーターは SQL_ATTR_ENLIST_IN_DTC、3 番目のパラメーターは (手順 3. で取得した) トランザクション オブジェクトである必要があります。  
  
5.  更新する SQL Server ごとに 1 回ずつ [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) を呼び出します。  
  
6.  MS DTC の OLE ITransaction::Commit 関数を呼び出して、MS DTC トランザクションをコミットします。 トランザクション オブジェクトは無効になります。  
  
 一連の MS DTC トランザクションを実行するには、手順 3. から手順 6. を繰り返します。  
  
 トランザクション オブジェクトへの参照を解放するには、MS DTC の OLE ITransaction::Return 関数を呼び出します。  
  
 MS DTC トランザクションで ODBC 接続を使用し、この接続をローカルの SQL Server トランザクションでも使用するには、[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) に SQL_DTC_DONE を指定して呼び出します。  
  
> [!NOTE]  
>  手順 4. と手順 5. で示した呼び出し方法の代わりに、SQL Server ごとに [SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md) と [SQLExecDirect](https://go.microsoft.com/fwlink/?LinkId=58399) を続けて呼び出すこともできます。  
  
## <a name="see-also"></a>参照  
 [トランザクションを実行する&#40;ODBC&#41;](../../database-engine/dev-guide/performing-transactions-odbc.md)  
  
  
