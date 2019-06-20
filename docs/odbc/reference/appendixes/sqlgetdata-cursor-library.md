---
title: SQLGetData (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetData function [ODBC], Cursor Library
ms.assetid: ff40c9c0-b847-4426-a099-1bff47e6e872
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1e3009b4e3bed6fc871ecfd1aab4e2af2f1f1c86
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63188767"
---
# <a name="sqlgetdata-cursor-library"></a>SQLGetData (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLGetData**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLGetData**を参照してください[SQLGetData 関数](../../../odbc/reference/syntax/sqlgetdata-function.md)します。  
  
 カーソル ライブラリを実装する**SQLGetData**最初に構築することによって、**選択**ステートメントを**場所**句の各バインドには、そのキャッシュに格納された値を列挙します。現在の行に列です。 実行して、**選択**し直すには、行と呼び出しステートメント**SQLGetData** (キャッシュ) ではなく、データ ソースからデータを取得するドライバー。  
  
> [!CAUTION]  
>  **場所**任意の行を識別する、別の行を特定または複数の行を識別する、現在の行を識別するために、カーソル ライブラリによって構築された句が失敗することができます。 詳細については、次を参照してください。[検索ステートメントの構築](../../../odbc/reference/appendixes/constructing-searched-statements.md)します。  
  
 SQL_UB_VARIABLE に SQL_ATTR_USE_BOOKMARKS ステートメントの属性が設定されている場合**SQLGetData**列 0 ブックマーク データを返すために呼び出すことができます。  
  
 呼び出す**SQLGetData**は次の制限を受けます。  
  
-   **SQLGetData**順方向専用カーソルを呼び出すことはできません。  
  
-   **SQLGetData**次の条件が満たされた場合にのみ呼び出すことができます。**選択**ステートメントは結果セットを生成、**選択**ステートメントに、結合が含まれていない、 **共用体**句、または**GROUP BY**は句と select リストで、別名または式を使用するすべての列にバインドされていない**SQLBindCol**します。  
  
-   カーソル ライブラリがの結果セットを実行する前に残りの部分をフェッチして、ドライバーは、1 つだけアクティブ ステートメントをサポートする場合、**選択**ステートメントおよび呼び出し**SQLGetData**します。
