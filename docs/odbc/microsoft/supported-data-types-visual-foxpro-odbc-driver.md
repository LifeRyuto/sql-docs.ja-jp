---
title: サポートされているデータ型 (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], data types
- FoxPro ODBC driver [ODBC], data types
- data types [ODBC], Visual FoxPro ODBC driver
ms.assetid: ab529cc6-d157-4b35-b6f9-6ffd09af098c
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e2d23ddc5fdd00db45aee235e96f13a8cf08082a
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080777"
---
# <a name="supported-data-types-visual-foxpro-odbc-driver"></a>サポートされるデータ型 (Visual FoxPro ODBC ドライバー)
ドライバーでサポートされているデータ型の一覧については、ODBC API と Microsoft Query を使用して説明します。  
  
## <a name="data-types-in-c-applications"></a>C アプリケーションでのデータ型  
 Visual FoxPro ODBC ドライバーでサポートされているデータ型の一覧を取得するには、C または C++ アプリケーションで[SQLGetTypeInfo](../../odbc/microsoft/sqlgettypeinfo-visual-foxpro-odbc-driver.md)関数を使用します。  
  
## <a name="data-types-in-applications-using-microsoft-query"></a>Microsoft Query を使用したアプリケーションのデータ型  
 アプリケーションで Microsoft Query を使用して Visual FoxPro データソースに新しいテーブルを作成する場合は、Microsoft Query によって [**テーブル定義の新規**作成] ダイアログボックスが表示されます。 [**フィールドの説明**] の [**種類**] ボックスに、単一の文字で表される、 [Visual FoxPro のフィールドのデータ型](../../odbc/microsoft/visual-foxpro-field-data-types.md)が一覧表示されます。
