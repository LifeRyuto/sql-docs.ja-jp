---
title: コミットとロールバックの動作 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 2ac8f012-e46d-41ca-81bb-e4a3246e3241
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 643d7d4174df66abfcee274c1f987e8f405d19b9
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68083341"
---
# <a name="commit-and-rollback-behavior"></a>動作のコミットとロールバック
サーバー Dbms 間の一般的な動作では、ステートメントがコミットまたはロールバックされるときに、カーソルを閉じ、準備されたステートメントを破棄します。 デスクトップデータベースは、カーソルを開いたままにして、準備されたステートメントを保持する可能性が高くなります。 詳細については、「 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明と、[カーソルおよび準備されたステートメントでのトランザクションの影響](../../../odbc/reference/develop-app/effect-of-transactions-on-cursors-and-prepared-statements.md)」の SQL_CURSOR_COMMIT_BEHAVIOR と SQL_CURSOR_ROLLBACK_BEHAVIOR のオプションを参照してください。
