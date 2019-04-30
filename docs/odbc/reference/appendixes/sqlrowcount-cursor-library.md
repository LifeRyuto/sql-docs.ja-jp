---
title: SQLRowCount (カーソル ライブラリ) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLRowCount function [ODBC], Cursor Library
ms.assetid: 781cf5a5-325e-4523-8633-d96d9e98277c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 9b3dcd9c348d83dad1e295e253cb37768fbb0abb
ms.sourcegitcommit: bd5f23f2f6b9074c317c88fc51567412f08142bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "63473046"
---
# <a name="sqlrowcount-cursor-library"></a>SQLRowCount (カーソル ライブラリ)
> [!IMPORTANT]  
>  この機能は、Windows の将来のバージョンで削除されます。 新しい開発作業でこの機能を使用しないようにして、現在この機能を使用しているアプリケーションの変更を検討してください。 ドライバーのカーソル機能を使用することをお勧めします。  
  
 このトピックの使用、 **SQLRowCount**カーソル ライブラリ内の関数。 に関する一般的な情報**SQLRowCount**を参照してください[Sqlrowcount](../../../odbc/reference/syntax/sqlrowcount-function.md)します。  
  
 アプリケーションを呼び出すと**SQLRowCount**カーソルに関連付けられているステートメントでカーソル ライブラリは、ドライバーから取得したデータの行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**位置指定の update または delete ステートメントに関連付けられているステートメントでカーソル ライブラリは、ステートメントによって影響を受ける行の数を返します。  
  
 アプリケーションを呼び出すと**SQLRowCount**後、**選択**ステートメントでは、カーソル ライブラリは、-1 を返します。
