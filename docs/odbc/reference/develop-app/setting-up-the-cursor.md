---
title: カーソルの設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- scrollable cursors [ODBC]
- cursors [ODBC], scrollable
- cursors [ODBC], creating
ms.assetid: b80afb0e-ef2f-408f-86f5-a392edd99a56
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 59ade343f282933e05619996b119bc08e2dfb2ab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62445914"
---
# <a name="setting-up-the-cursor"></a>カーソルの設定
設定の結果を作成するステートメントを実行する前に、アプリケーションは、カーソルの種類を指定できます。 これは、SQL_ATTR_CURSOR_TYPE ステートメント属性を持つ。 アプリケーションが、型が明示的に指定しない場合は、順方向専用カーソルが使用されます。 混合カーソルを取得するには、アプリケーションは、キーセット ドリブン カーソルを指定しますが、結果セットのサイズより小さいキーセットのサイズを宣言します。  
  
 キーセット ドリブン、混合カーソルの場合、アプリケーションは、キーセットのサイズにも指定できます。 これは、SQL_ATTR_KEYSET_SIZE ステートメント属性を持つ。 キーセットのサイズが 0 で、既定値に設定されている場合は、キーセットのサイズは、結果セットのサイズに設定され、キーセット ドリブン カーソルが使用されます。 カーソルが開かれた後、キーセットのサイズを変更できます。  
  
 アプリケーションでは、行セットのサイズを設定できますまた詳細については、次を参照してください。[ブロック カーソルを使用して](../../../odbc/reference/develop-app/using-block-cursors.md)、このセクションでは以前のバージョン。
