---
title: SQL Server のメッセージ結果 |Microsoft Docs
description: SQL Server のメッセージ結果
ms.custom: ''
ms.date: 06/14/2018
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: connectivity
ms.topic: reference
helpviewer_keywords:
- OLE DB Driver for SQL Server, errors
- errors [OLE DB], SQL Server message results
- OLE DB error handling, SQL Server message results
author: pmasl
ms.author: pelopes
manager: jroth
ms.openlocfilehash: 9098994ac5349fa9747c952e66eb902231956a5c
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802847"
---
# <a name="sql-server-message-results"></a>SQL Server のメッセージ結果
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]

[!INCLUDE[Driver_OLEDB_Download](../../../includes/driver_oledb_download.md)]

  次の [!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントでは、OLE DB Driver for SQL Server の行セットや、ステートメント実行時に処理された行カウントは生成されません。  
  
-   PRINT  
  
-   重大度が 10 以下の RAISERROR  
  
-   DBCC  
  
-   SET SHOWPLAN  
  
-   SET STATISTICS  
  
 上記のステートメントでは、行セットや行数の結果が返されるのではなく、ステートメントから 1 つ以上の情報メッセージが返されるか、[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] から情報メッセージが返されます。 実行に成功、OLE DB Driver for SQL Server が S_OK を返すし、メッセージは、OLE DB Driver for SQL Server コンシューマーを使用できます。  
  
 OLE DB Driver for SQL Server が S_OK が返され、1 つまたは複数情報メッセージの多くの実行に使用可能なの[!INCLUDE[tsql](../../../includes/tsql-md.md)]ステートメント、または、OLE DB Driver for SQL Server メンバー関数のコンシューマー実行します。  
  
 OLE DB Driver for SQL Server のコンシューマーがクエリ テキストの動的な指定を許可する場合、メンバー関数を実行するたびにエラー インターフェイスをチェックする必要があります。このチェックは、リターン コードの値、返される **IRowset** インターフェイス参照や **IMultipleResults** インターフェイス参照の有無、および処理された行数に関係なく行う必要があります。  
  
## <a name="see-also"></a>参照  
 [エラー](../../oledb/ole-db-errors/errors.md)  
  
  
