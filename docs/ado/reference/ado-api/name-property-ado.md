---
title: Name プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Parameter::Name
- Field20::Name
helpviewer_keywords:
- Name property [ADO]
ms.assetid: cfd0e29c-8310-44ab-85c3-5761184b865d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a919bb377eee2da1c3c1a65e85ddfb9807ed8d50
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67918036"
---
# <a name="name-property-ado"></a>Name プロパティ (ADO)
オブジェクトの名前を示します。  
  
## <a name="settings-and-return-values"></a>設定と戻り値  
 オブジェクトの名前を示す**文字列**値を設定または返します。  
  
## <a name="remarks"></a>解説  
 **Name プロパティを**使用して、**コマンド**、**プロパティ**、**フィールド**、または**パラメーター**オブジェクトの名前を割り当てるか、名前を取得します。  
  
 この値は、 **Command**オブジェクトでは読み取り/書き込みが可能で、**プロパティ**オブジェクトでは読み取り専用です。  
  
 **Field**オブジェクトの場合、通常、**名前**は読み取り専用です。 ただし、[レコード](../../../ado/reference/ado-api/record-object-ado.md)の[フィールド](../../../ado/reference/ado-api/fields-collection-ado.md)コレクションに追加された新しい**フィールド**オブジェクトの場合、 **Name**は、**フィールド**の[Value](../../../ado/reference/ado-api/value-property-ado.md)プロパティが指定され、データプロバイダーが**フィールド**コレクションの[Update](../../../ado/reference/ado-api/update-method.md)メソッドを呼び出すことによって新しい**フィールド**を正常に追加した後にのみ、読み取り/書き込みになります。  
  
 [Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションにまだ追加されていない**パラメーター**オブジェクトの場合、 **Name**プロパティは読み取り/書き込み可能です。 追加された**パラメーター**オブジェクトおよびその他すべてのオブジェクトについては、 **Name**プロパティは読み取り専用です。 名前はコレクション内で一意である必要はありません。  
  
 オブジェクトの**name**プロパティは、序数参照によって取得できます。その後、オブジェクトを名前で直接参照できます。 たとえば、がを`rstMain.Properties(20).Name`生成`Updatability`した場合、このプロパティをと`rstMain.Properties("Updatability")`して参照できます。  
  
## <a name="applies-to"></a>適用対象  
  
|||  
|-|-|  
|[Command オブジェクト (ADO)](../../../ado/reference/ado-api/command-object-ado.md)|[Field オブジェクト](../../../ado/reference/ado-api/field-object.md)|  
|[Parameter オブジェクト](../../../ado/reference/ado-api/parameter-object.md)|[Property オブジェクト (ADO)](../../../ado/reference/ado-api/property-object-ado.md)|  
  
## <a name="see-also"></a>参照  
 [Attributes と Name プロパティの例 (VB)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vb.md)   
 [Attributes と Name プロパティの例 (VC + +)](../../../ado/reference/ado-api/attributes-and-name-properties-example-vc.md)   
