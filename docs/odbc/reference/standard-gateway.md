---
title: Standard ゲートウェイ |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC [ODBC], database access
- SQL [ODBC], database access
- database access [ODBC]
- standardizing database access [ODBC], gateways
- standard gateways [ODBC]
- gateways [ODBC]
ms.assetid: b8341492-2141-4bab-80bd-f2752223079e
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 8120f3cda584240b0b58ed5d6758621b18fe44d3
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070477"
---
# <a name="standard-gateway"></a>標準のゲートウェイ
*ゲートウェイ*とは、ある DBMS を別の DBMS のように表示するソフトウェアのことです。 つまり、ゲートウェイは、単一の DBMS のプログラミングインターフェイス、SQL 文法、データストリームプロトコルを受け入れ、それを非表示の DBMS のプログラミングインターフェイス、SQL 文法、データストリームプロトコルに変換します。 たとえば、Microsoft® SQL Server™を使用するように作成されたアプリケーションは、マイクロ Decisionware DB2 ゲートウェイを介して DB2 データにアクセスすることもできます。この製品を使うと、DB2 は SQL Server のようになります。 ゲートウェイを使用する場合は、ターゲットデータベースごとに異なるゲートウェイを作成する必要があります。  
  
 ゲートウェイは、Dbms 間のアーキテクチャの違いによって制限されますが、標準化に適しています。 ただし、すべての dbms が、1つの DBMS のプログラミングインターフェイス、SQL 文法、データストリームプロトコルで標準化されている場合は、DBMS を標準として選択する必要がありますか。 確かに、商用の DBMS ベンダーは、競合他社の製品に対して標準化に同意することはありません。 また、標準的なプログラミングインターフェイス、SQL 文法、データストリームプロトコルが開発されている場合、ゲートウェイは必要ありません。
