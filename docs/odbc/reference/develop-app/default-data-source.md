---
title: 既定のデータ ソース |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- data sources [ODBC], connection functions
- connecting to data source [ODBC], default data source
- functions [ODBC], data source or driver connections
- data sources [ODBC], default
- default data source [ODBC]
- connecting to data source [ODBC], functions
- connecting to driver [ODBC], default data source
- connecting to driver [ODBC], functions
- connection functions [ODBC]
- ODBC drivers [ODBC], connection functions
ms.assetid: dd473cc6-f051-4aa0-ab14-3dd1b37fe99e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 909f9b3e7c8087add8eb66ca2f5c15253026304c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63267649"
---
# <a name="default-data-source"></a>既定のデータ ソース
ドライバーは、特定のケースで、アプリケーションで明示的に指定されない 1 つで、既定のデータ ソースと呼ばれる、データ ソースを選択できます。  
  
-   呼び出しで**SQLConnect**場所、 *ServerName*引数が長さ 0 の文字列、null ポインター、または既定値。  
  
-   呼び出しで**SQLDriverConnect**場所*InConnectionString*いずれかを指定します**DSN**= 既定またはを指定します、 **DSN**キーワード、システム情報に含まれていないデータ ソース。  
  
 ドライバーで定義された既定のデータ ソースを指定する方法。 これは管理操作を伴う可能性があり、ユーザーによって異なります。
