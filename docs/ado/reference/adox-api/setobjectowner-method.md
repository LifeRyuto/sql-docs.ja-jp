---
title: SetObjectOwner メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- _Catalog::SetObjectOwner
- _Catalog::raw_SetObjectOwner
helpviewer_keywords:
- SetObjectOwner method [ADOX]
ms.assetid: e5170a37-9d6e-43db-bfb6-9b6631fa3048
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 50a02898c1694fa43b8bf522a1a1bca65300efda
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67965236"
---
# <a name="setobjectowner-method"></a>SetObjectOwner メソッド
[カタログ](../../../ado/reference/adox-api/catalog-object-adox.md)内のオブジェクトの所有者を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
Catalog.SetObjectOwner ObjectName, ObjectType, OwnerName [,ObjectTypeId]  
```  
  
#### <a name="parameters"></a>パラメーター  
 *ObjectName*  
 所有者を指定するオブジェクトの名前を示す**文字列**値です。  
  
 *ObjectType*  
 Owner 型を指定する[Objecttypeenum](../../../ado/reference/adox-api/objecttypeenum.md)定数の1つである**Long**値。  
  
 *OwnerName*  
 オブジェクトを所有する[ユーザー](../../../ado/reference/adox-api/user-object-adox.md)または[グループ](../../../ado/reference/adox-api/group-object-adox.md)の[名前](../../../ado/reference/adox-api/name-property-adox.md)を指定する**文字列**値。  
  
 *ObjectTypeId*  
 省略可能。 OLE DB 仕様で定義されていないプロバイダーオブジェクト型の GUID を示す**バリアント**値です。 *ObjectType*が**Adpermobjproviderspecific**に設定されている場合、このパラメーターは必須です。それ以外の場合は使用されません。  
  
## <a name="remarks"></a>解説  
 プロバイダーがオブジェクトの所有者の指定をサポートしていない場合、エラーが発生します。  
  
## <a name="applies-to"></a>適用対象  
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)  
  
## <a name="see-also"></a>参照  
 [GetObjectOwner メソッドと SetObjectOwner メソッドの例 (VB)](../../../ado/reference/adox-api/getobjectowner-and-setobjectowner-methods-example-vb.md)   
 [GetObjectOwner メソッド (ADOX)](../../../ado/reference/adox-api/getobjectowner-method-adox.md)
