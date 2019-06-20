---
title: SQLBulkOperations による行のフェッチ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data updates [ODBC], bookmarks
- SQLBulkOperations function [ODBC], fetching rows
- data updates [ODBC], SQLBulkOperations
- bookmarks [ODBC]
- updating data [ODBC], bookmarks
- updating data [ODBC], SQLBulkOperations
ms.assetid: 0efee2d6-ce94-411e-9976-97ba28b8da37
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a99592210ff315db026d60b8743d4a3bca13c969
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63061630"
---
# <a name="fetching-rows-with-sqlbulkoperations"></a>SQLBulkOperations による行のフェッチ
呼び出しでブックマークを使用して行セットにデータは再フェッチ**SQLBulkOperations します。** フェッチする行は、バインドされたブックマーク列内のブックマークによって識別されます。 SQL_COLUMN_IGNORE の値を持つ列はフェッチされません。  
  
 一括フェッチを実行する**SQLBulkOperations**アプリケーションは、次を実行します。  
  
1.  取得し、更新するすべての行のブックマークをキャッシュします。 ブックマークは配列に格納されている 1 つ以上のブックマークが存在し、列方向のバインドを使用した場合1 つ以上のブックマークが存在し、行方向のバインドを使用した場合、それらのブックマークは、行の構造体の配列に格納されます。  
  
2.  SQL_ATTR_ROW_ARRAY_SIZE ステートメント属性をフェッチする行の数に設定し、ブックマークの値、または列 0 へのブックマークの配列を含むバッファーをバインドします。  
  
3.  必要に応じて、各列の長さ/インジケーター バッファーの値を設定します。 これは、SQL_NTS またはデータのバイト長のバイナリのバッファーを NULL に設定する列の SQL_NULL_DATA バインドされている列のデータのバイト長の文字列のバッファーにバインドされている列です。 アプリケーションでは、(存在する場合、既定値に設定するのにはそれらの列または SQL_COLUMN_IGNORE を NULL (1 つでない場合) の長さ/インジケーター バッファーの値を設定します。  
  
4.  呼び出し**SQLBulkOperations**で、*操作*引数 SQL_FETCH_BY_BOOKMARK に設定します。  
  
 特定の列に対して実行するアプリケーションで、操作を防ぐために、行操作配列を使用する必要はありません。 アプリケーションでは、バインドされたブックマーク配列にそれらの行のブックマークのみをコピーすることでフェッチする行を選択します。
