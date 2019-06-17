---
title: 診断 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC]
- functions [ODBC], diagnostic information
- diagnostic information [ODBC], about diagnostic information
ms.assetid: 450abd88-90a1-4fbc-b417-8efbdd8e1dea
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 72e79d377371277720e2fcc15a31ce715693d832
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63242295"
---
# <a name="diagnostics"></a>診断
ODBC 関数では、2 つの方法で診断情報を返します。 リターン コードでは、全体的な成功または失敗、関数の診断レコードが、関数に関する詳細情報を提供に示します。 関数が成功した場合でも、少なくとも 1 つの診断レコードのヘッダー レコード - が返されます。  
  
 診断情報は、ハード コーディングされた SQL ステートメントで無効なハンドルなどのプログラミング エラーや構文エラーをキャッチする開発時に使用されます。 実行時エラーとデータの切り捨て、アクセス違反、構文エラーなどの警告をユーザーが入力した SQL ステートメントでキャッチする実行時に使用されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [リターン コード](../../../odbc/reference/develop-app/return-codes-odbc.md)  
  
-   [診断レコード](../../../odbc/reference/develop-app/diagnostic-records.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の使用](../../../odbc/reference/develop-app/using-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [SQLGetDiagRec および SQLGetDiagField の実装](../../../odbc/reference/develop-app/implementing-sqlgetdiagrec-and-sqlgetdiagfield.md)  
  
-   [診断処理の例](../../../odbc/reference/develop-app/diagnostic-handling-examples.md)
