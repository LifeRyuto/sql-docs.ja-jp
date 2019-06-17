---
title: SQLTransact 関数 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLTransact
apilocation:
- sqlsrv32.dll
apitype: dllExport
f1_keywords:
- SQLTransact
helpviewer_keywords:
- SQLTransact function [ODBC]
ms.assetid: 496249e0-8eff-4c60-8358-5543bc3ead9c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b76b7a550211522c2b2100776b88f311abb2b932
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63233349"
---
# <a name="sqltransact-function"></a>SQLTransact 関数
**準拠**  
 バージョンが導入されました。ODBC 1.0 規格に準拠します。非推奨  
  
 **まとめ**  
 ODBC 3。*x*、ODBC 2 *.x*関数**SQLTransact**置き換わりました**SQLEndTran**します。 詳細については、次を参照してください。 [SQLEndTran](../../../odbc/reference/syntax/sqlendtran-function.md)します。  
  
> [!NOTE]  
>  ODBC 3.8 にで導入された、SQL_ASYNC_DBC_FUNCTION_ENABLE 属性がサポートされていない**SQLTransact**します。 接続ハンドルでの非同期操作を使用してアプリケーションを使用する必要があります**SQLEndTran**します。  
  
## <a name="see-also"></a>参照  
 [ODBC API リファレンス](../../../odbc/reference/syntax/odbc-api-reference.md)   
 [ODBC ヘッダー ファイル](../../../odbc/reference/install/odbc-header-files.md)
