---
title: InheritTypeEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- InheritTypeEnum
helpviewer_keywords:
- InheritTypeEnum enumeration [ADOX]
ms.assetid: c2f6ce79-c4b3-4d40-ac95-21025208f991
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b17bdd7204ec52ef5a2fc27d7bc364be7f017189
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/05/2019
ms.locfileid: "66706499"
---
# <a name="inherittypeenum"></a>InheritTypeEnum
オブジェクトに設定されたアクセス許可を継承する方法を指定します。 [SetPermissions](../../../ado/reference/adox-api/setpermissions-method-adox.md)します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adInheritBoth**|3|オブジェクトと、プライマリ オブジェクトに含まれるその他のコンテナーの両方のエントリを継承します。|  
|**adInheritContainers**|2|プライマリ オブジェクトに含まれる他のコンテナーでは、エントリを継承します。|  
|**adInheritNone**|0|既定値です。 継承は行われません。|  
|**adInheritNoPropagate**|4|**AdInheritObjects**と**adInheritContainers**フラグは継承されたエントリには反映されません。|  
|**adInheritObjects**|1|コンテナー内の非コンテナー オブジェクトは、アクセス許可を継承します。|  
  
## <a name="applies-to"></a>適用対象  
 [SetPermissions メソッド (ADOX)](../../../ado/reference/adox-api/setpermissions-method-adox.md)
