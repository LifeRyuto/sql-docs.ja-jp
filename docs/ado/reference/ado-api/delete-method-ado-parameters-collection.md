---
title: Delete メソッド (ADO Parameters コレクション) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _DynaCollection::Delete
- _DynaCollection::raw_Delete
helpviewer_keywords:
- Delete method [ADO]
ms.assetid: 160c575e-df63-4ade-a2d3-5fd8f72e70cc
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 965ef1bc84961e3358c530180bfe4e99249b0bc7
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933172"
---
# <a name="delete-method-ado-parameters-collection"></a>Delete メソッド (ADO Parameters コレクション)
[Parameters](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクションからオブジェクトを削除します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Parameters.Delete Index  
```  
  
#### <a name="parameters"></a>パラメーター  
 *化*  
 削除するオブジェクトの名前、またはコレクション内のオブジェクトの序数 (index) を含む**文字列**値です。  
  
## <a name="remarks"></a>解説  
 コレクションに対して**Delete**メソッドを使用すると、コレクション内のいずれかのオブジェクトを削除できます。 このメソッドは、 [Command](../../../ado/reference/ado-api/command-object-ado.md)オブジェクトの**Parameters**コレクションでのみ使用できます。 **Delete**メソッドを呼び出すときは、[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトの[Name](../../../ado/reference/ado-api/name-property-ado.md)プロパティまたはそのコレクションインデックスを使用する必要があります。オブジェクト変数は有効な引数ではありません。  
  
## <a name="applies-to"></a>適用対象  
 [Parameters コレクション (ADO)](../../../ado/reference/ado-api/parameters-collection-ado.md)  
  
## <a name="see-also"></a>参照  
 [Delete メソッド (ADO Fields コレクション)](../../../ado/reference/ado-api/delete-method-ado-fields-collection.md)   
 [Delete メソッド (ADO Recordset)](../../../ado/reference/ado-api/delete-method-ado-recordset.md)   
 [DeleteRecord メソッド (ADO)](../../../ado/reference/ado-api/deleterecord-method-ado.md)
