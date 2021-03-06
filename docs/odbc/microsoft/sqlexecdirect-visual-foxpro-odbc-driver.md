---
title: SQLExecDirect (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e701340217a885fbf1e3372c33ed1a8cfdb21457
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68053850"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: コアレベル  
  
 新しい[準備可能 SQL ステートメント](../../odbc/microsoft/visual-foxpro-terminology.md)を実行します。 ステートメントにパラメーターが存在する場合、Visual FoxPro ODBC ドライバーはパラメーターマーカー変数の現在の値を使用します。  
  
 一度に複数の SQL ステートメントを送信するバッチコマンドを作成するには、セミコロン;) () を使用します。バッチ内の各 SQL ステートメントを分離する場合はです。  
  
 テーブル、ビュー、またはフィールドの名前にスペースが含まれている場合は、名前を後方引用符で囲みます。 たとえば、データベースに My Table という名前のテーブルとフィールド My Field が含まれている場合は、識別子の各要素を次のように囲みます。  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md) 」を参照してください。
