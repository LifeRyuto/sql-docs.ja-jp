---
title: キューブ属性のプロパティの定義 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f7e2ab2374955710452f1ba1cba91e3a4d8ff8c1
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63025482"
---
# <a name="define-cube-attribute-properties"></a>キューブ属性のプロパティの定義
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  キューブ属性のプロパティにより、同じデータベース ディメンションに基づいたキューブ ディメンション内のディメンション属性に一意の設定を指定できます。 次の表では、キューブ属性のプロパティについて説明します。  
  
|プロパティ|説明|  
|--------------|-----------------|  
|**AggregationUsage**|集計デザイン ウィザードによる属性の集計の設計方法を指定します。 既定値は **Default**です。 このプロパティは、以下の値をとります。<br /><br /> **Default**:<br />                    集計デザイン ウィザードは、属性の種類に基づいて既定のルール (キーの場合は Full、その他の場合は Unrestricted) を適用します。<br /><br /> **[なし]**:<br />                    キューブの集計にはこの属性を含めないでください。<br /><br /> **Unrestricted**:<br />                    集計デザイン ウィザードに対して制限を適用しません。<br /><br /> **Full**:<br />                    キューブのすべての集計にこの属性が含まれている必要があります。|  
|**AttributeHierarchyEnabled**|属性階層をこのキューブ ディメンションで有効にするかどうかを識別します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して無効にすることができます。 この設定は、基になる属性階層が無効になっている場合には影響を受けません。 既定値は **True**です。|  
|**OptimizedState**|属性階層をこのキューブ ディメンションに対して最適化するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールに対して最適化できます。 この設定は、基になる属性階層が最適化されていない場合には影響を受けません。 既定値は **FullyOptimized**です。 このプロパティは、以下の値をとります。<br /><br /> **FullyOptimized**:インスタンスは、階層のインデックスを構築し、クエリ パフォーマンスを改善します。 これが既定値です。<br /><br /> **NotOptimized**:<br />                    インスタンスは追加のインデックスを構築しません。|  
|**AttributeHierarchyVisible**|属性階層をこのキューブ ディメンションで表示するかどうかを示します。 これによって属性階層を特定のキューブまたはディメンション ロールで表示できます。 この設定は、基になる属性階層が表示されていない場合には影響を受けません。 既定値は **True**です。|  
|**AttributeID**|属性の一意識別子 (ID) を示します。|  
  
## <a name="see-also"></a>参照  
 [キューブ ディメンションのプロパティの定義](../../analysis-services/multidimensional-models/define-cube-dimension-properties.md)   
 [キューブ階層のプロパティの定義](../../analysis-services/multidimensional-models/define-cube-hierarchy-properties.md)  
  
  
