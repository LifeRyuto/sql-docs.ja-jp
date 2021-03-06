---
title: ステートメントの実行 (ODBC) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, statements
- statements [ODBC]
- ODBC applications, statements
- statements [ODBC], executing
ms.assetid: 063fc40d-ff81-490d-9c9b-2faefb729f37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1517e17a7b0ecaf9137e3af21e076dacc2fd98f3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68207059"
---
# <a name="executing-statements-odbc"></a>ステートメントの実行 (ODBC)
  Native [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] Client ODBC ドライバーには、 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]データベース内で SQL ステートメントを実行するためのさまざまな方法が用意されています。  
  
-   直接実行  
  
-   準備実行  
  
 直接実行では、ステートメントを[!INCLUDE[tsql](../../../includes/tsql-md.md)]含む文字列を作成し、 **SQLExecDirect**関数を使用して実行するために送信します。 準備実行では、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントを含む文字列を作成してから、そのステートメントを 2 段階に分けて実行します。 最初の段階では、 [SQLPrepare 関数](https://go.microsoft.com/fwlink/?LinkId=59360)関数を使用して、の[!INCLUDE[ssDE](../../../includes/ssde-md.md)]ステートメントの実行プランを解析およびコンパイルします。 2番目の段階では、 **Sqlexecute**関数を使用して、事前に準備された実行プランを実行します。 この方法では、各実行にかかる解析とコンパイルのオーバーヘッドが抑制されます。 準備実行は、通常、同一のパラメーター化された SQL ステートメントを繰り返し実行するアプリケーションで使用されます。  
  
 どちらの実行方法でも、[!INCLUDE[tsql](../../../includes/tsql-md.md)] ステートメントまたは SQL ステートメントのバッチを 1 つ実行でき、ステートメントからストアド プロシージャを呼び出すことができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [直接実行](direct-execution.md)  
  
-   [準備実行](prepared-execution.md)  
  
-   [手順](procedures.md)  
  
-   [ステートメントのバッチ](batches-of-statements.md)  
  
-   [ISO オプションの効果](effects-of-iso-options.md)  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;クエリの実行](../executing-queries-odbc.md)  
  
  
