---
title: LockTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- LockTypeEnum
helpviewer_keywords:
- LockTypeEnum enumeration [ADO]
ms.assetid: d2894eaf-4450-4ace-aa51-c8b875fd3010
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 0ae822794b1b06a975e1cc3cd397b5a5f00036dc
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918256"
---
# <a name="locktypeenum"></a>LockTypeEnum
編集中にレコードに適用されるロックの種類を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adLockBatchOptimistic**|4|オプティミスティックバッチ更新を示します。 バッチ更新モードでは必須です。|  
|**adLockOptimistic**|3|オプティミスティックロック、レコードごとのレコードを示します。 プロバイダーはオプティミスティックロックを使用し、 [Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出したときにのみレコードをロックします。|  
|**adLockPessimistic**|2|ペシミスティックロック、レコードごとのレコードを示します。 プロバイダーは、レコードを正常に編集するために必要な処理を実行します。通常は、編集後すぐにデータソースのレコードをロックします。|  
|**adLockReadOnly**|1 で保護されたプロセスとして起動されました|読み取り専用レコードを示します。 データを変更することはできません。|  
|**adLockUnspecified**|-1|はロックの種類を指定していません。 複製の場合、複製は元と同じロックの種類で作成されます。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums. BATCHOPTIMISTIC|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
|AdoEnums|  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Clone メソッド (ADO)](../../../ado/reference/ado-api/clone-method-ado.md)|[LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)|  
|[Open メソッド (ADO Recordset)](../../../ado/reference/ado-api/open-method-ado-recordset.md)|[WillExecute イベント (ADO)](../../../ado/reference/ado-api/willexecute-event-ado.md)|
