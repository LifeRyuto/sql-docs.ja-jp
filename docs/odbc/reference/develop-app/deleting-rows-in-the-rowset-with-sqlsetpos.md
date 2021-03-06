---
title: SQLSetPos | を使用して行セット内の行を削除するMicrosoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetPos function [ODBC], deleting rows
- updating data [ODBC], SQLSetPos
- data updates [ODBC], SQLSetPos
ms.assetid: 3117a47d-e179-4f76-89d0-656582f1c9bb
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e39b70f92f7b239b011cdd4fdd6abd36c27561c2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68076803"
---
# <a name="deleting-rows-in-the-rowset-with-sqlsetpos"></a>SQLSetPos による行セットの行の削除
**SQLSetPos**の削除操作により、データソースはテーブルの選択された1つ以上の行を削除します。 **Sqlsetpos**を使用して行を削除するには、アプリケーションは、*操作*が SQL_DELETE に設定された**sqlsetpos**を呼び出し、 *RowNumber*を削除する行の番号に設定します。 *RowNumber*が0の場合、行セット内のすべての行が削除されます。  
  
 **SQLSetPos**が戻った後、削除された行が現在の行になり、その状態が SQL_ROW_DELETED になります。 この行は、 **SQLGetData**または**SQLSetPos**の呼び出しなど、他の位置指定操作では使用できません。  
  
 行セットのすべての行を削除すると (*RowNumber*が0の場合)、アプリケーションでは、 **SQLSetPos**の更新操作と同じように、行操作配列を使用してドライバーが特定の行を削除できないようにすることができます。 (「 [SQLSetPos を使用](../../../odbc/reference/develop-app/updating-rows-in-the-rowset-with-sqlsetpos.md)して行セットの行を更新する」を参照してください)。  
  
 削除対象の各行は、行セット内に存在する行でなければなりません。 フェッチによってアプリケーションバッファーがいっぱいになっていて、行の状態配列が保持されている場合は、行の各位置の値を SQL_ROW_DELETED、SQL_ROW_ERROR、または SQL_ROW_NOROW にすることはできません。
