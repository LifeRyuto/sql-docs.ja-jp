---
title: '手順 2: アプリケーションの初期化 |Microsoft Docs'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- initializing applications [ODBC]
- application process [ODBC], initializing applications
ms.assetid: 23a7a230-ae2c-4a5e-9760-d2e17f92c389
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: b0d25173dc8dc14aa1ed41a4a88496ef654e2ff0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47850927"
---
# <a name="step-2-initialize-the-application"></a>ステップ 2: アプリケーションの初期化
2 番目の手順は、アプリケーションを初期化するためには次の図に示すようにします。 正確にどのようなここでは、アプリケーションによって異なります。  
  
 ![ODBC アプリケーションの初期化を示しています](../../../odbc/reference/develop-app/media/pr12.gif "pr12。")  
  
 この時点では使用する一般的な**SQLGetInfo**ドライバーの機能を検出します。 詳細については、[使用するデータベース機能を検討して](../../../odbc/reference/develop-app/considering-database-features-to-use.md)を参照してください。  
  
 すべてのアプリケーションでのステートメント ハンドルを割り当てる必要があります**SQLAllocHandle**、多くのアプリケーションで、カーソルの種類などのステートメント属性を設定して**SQLSetStmtAttr**します。 詳細については、[ステートメント ハンドルの割り当て](../../../odbc/reference/develop-app/allocating-a-statement-handle-odbc.md)と[ステートメント属性](../../../odbc/reference/develop-app/statement-attributes.md)を参照してください。
