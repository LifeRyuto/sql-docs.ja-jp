---
title: 国際化サポート (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 50d65520e74a4e11bada88795fedc0b2f2e82628
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853101"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>国際化サポート (Visual FoxPro ODBC ドライバー)
Microsoft Visual FoxPro ODBC ドライバーがサポートされています。  
  
-   2 バイト文字セット (DBCS)  
  
-   複数の照合順序  
  
 照合順序を定義、*並べ替え順序*Visual FoxPro テーブルまたはデータベースに格納されています。 既定では、ドライバーは、オペレーティング システムの言語バージョンをサポートする照合順序を使用するよう構成します。  
  
 サポートされている照合順序の一覧は、[COLLATE 設定](../../odbc/microsoft/set-collate-command.md)を参照してください。  
  
## <a name="locale"></a>ロケール (locale)  
 特定の言語と国/地域に対応する情報のセット。 ロケールでは、桁区切り記号、日付と時刻の形式、および文字の並べ替え順序などの特定の設定を示します。  
  
## <a name="sort-order"></a>並べ替え順 (sort order)  
 並べ替え順序は、別の並べ替え規則を組み込む*ロケール*s、それらの言語でデータを正しく並べ替えるにすることができます。 Visual FoxPro では、現在の並べ替え順序は、文字式の比較と、レコードが表示されるインデックスまたはテーブルの並べ替え順序の結果を決定します。
