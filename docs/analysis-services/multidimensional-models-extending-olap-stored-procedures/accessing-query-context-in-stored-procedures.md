---
title: ストアド プロシージャのクエリ コンテキストへのアクセス |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: olap
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 1679b5ddaf2c3abefb6da4e89e97e84193593630
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68209397"
---
# <a name="accessing-query-context-in-stored-procedures"></a>ストアド プロシージャのクエリ コンテキストへのアクセス
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  ストアド プロシージャの実行コンテキストは、ストアド プロシージャとしてのコード内で使用できる、**コンテキスト**ADOMD.NET サーバー オブジェクト モデルのオブジェクト。 これは、読み取り専用のコンテキストであり、ストアド プロシージャによって変更することはできません。 このオブジェクトでは次のプロパティを使用できます。  
  
|プロパティ|型|説明|  
|--------------|----------|-----------------|  
|**CurrentCube**|Cube|現在のクエリ コンテキストのキューブです。|  
|**CurrentDatabaseName**|String|現在のデータベースの識別子です。|  
|**CurrentConnection**|接続|現在のコンテキストの接続オブジェクトへの参照です。|  
|**パス**|整数型|現在のコンテキストのパス番号です。|  
  
 **コンテキスト**ストアド プロシージャは、多次元式 (MDX) オブジェクト モデルを使用すると、オブジェクトが存在します。 MDX オブジェクト モデルがクライアントで使用されている場合には利用できません。 **コンテキスト**オブジェクトが明示的に渡されるか、ストアド プロシージャによって返されます。 ストアド プロシージャの実行中に利用できます。  
  
## <a name="see-also"></a>関連項目  
 [多次元モデルのアセンブリの管理](../../analysis-services/multidimensional-models/multidimensional-model-assemblies-management.md)   
 [ストアド プロシージャの定義](../../analysis-services/multidimensional-models-extending-olap-stored-procedures/defining-stored-procedures.md)  
  
  
