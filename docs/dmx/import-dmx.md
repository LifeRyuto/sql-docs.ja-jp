---
title: IMPORT (DMX) |Microsoft Docs
ms.date: 06/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: dmx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4987701deb466148253c8418c88683d2dbfbc16b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62506069"
---
# <a name="import-dmx"></a>IMPORT (DMX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  マイニング モデルまたはマイニング構造をサーバーに Analysis Services Backup File (.abf) ファイルから読み込みます。  
  
## <a name="syntax"></a>構文  
  
```  
  
IMPORT FROM <filename>  
```  
  
## <a name="arguments"></a>引数  
 *filename*  
 インポートするファイルの名前と場所を表す文字列。  
  
## <a name="remarks"></a>コメント  
 オブジェクトが指定されていない場合、.dmb ファイルの内容全体が読み込まれます。 .dmb ファイルに、サーバー上に存在しないデータベースが含まれている場合、そのデータベースが作成されます。  
  
 オブジェクトをエクスポートまたはインポートするには、データベースまたはサーバーの管理者である必要があります。  
  
## <a name="import-from-file-example"></a>ファイルからインポートする例  
 次の例では、アソシエーション モデルおよび構造体を現在のサーバーを含むファイルの内容全体をインポートします。  
  
```  
IMPORT FROM 'C:\TEMP\Association_NEW.dmb'  
```  
  
## <a name="see-also"></a>参照  
 [データ マイニング拡張機能&#40;DMX&#41;データ定義ステートメント](../dmx/dmx-statements-data-definition.md)   
 [データ マイニング拡張機能&#40;DMX&#41;データ操作ステートメント](../dmx/dmx-statements-data-manipulation.md)   
 [データ マイニング拡張機能&#40;DMX&#41;ステートメント リファレンス](../dmx/data-mining-extensions-dmx-statements.md)   
 [エクスポート&AMP;#40;DMX&AMP;#41;](../dmx/export-dmx.md)   
 [データ マイニング オブジェクトのエクスポートおよびインポート](../analysis-services/data-mining/export-and-import-data-mining-objects.md)  
  
  
