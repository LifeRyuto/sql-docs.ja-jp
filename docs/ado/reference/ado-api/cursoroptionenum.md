---
title: カーソルオプションの列挙 |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorOptionEnum
helpviewer_keywords:
- CursorOptionEnum enumeration [ADO]
ms.assetid: 4e10cda7-ce81-4466-94c2-844d38191cf1
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 1d5cc44950754c4b63e644d2d9210edcc94bd9ff
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67933265"
---
# <a name="cursoroptionenum"></a>CursorOptionEnum
[サポート](../../../ado/reference/ado-api/supports-method.md)メソッドがテストする必要がある機能を指定します。  
  
|常時|値|[説明]|  
|--------------|-----------|-----------------|  
|**adAddNew**|0x1000400|では、 [AddNew](../../../ado/reference/ado-api/addnew-method-ado.md)メソッドをサポートして、新しいレコードを追加します。|  
|**adApproxPosition**|0x4000|では、 [AbsolutePosition](../../../ado/reference/ado-api/absoluteposition-property-ado.md)プロパティと[AbsolutePage](../../../ado/reference/ado-api/absolutepage-property-ado.md)プロパティがサポートされています。|  
|**adBookmark**|0x2000|は、 [Bookmark](../../../ado/reference/ado-api/bookmark-property-ado.md)プロパティをサポートして、特定のレコードにアクセスできるようにします。|  
|**adDelete**|0x1000800|レコードを削除するための[delete](../../../ado/reference/ado-api/delete-method-ado-recordset.md)メソッドをサポートします。|  
|**adFind**|0x80000|では、[レコードセット](../../../ado/reference/ado-api/recordset-object-ado.md)内の行を検索するための[Find](../../../ado/reference/ado-api/find-method-ado.md)メソッドがサポートされています。|  
|**adHoldRecords**|0x100|すべての保留中の変更をコミットせずに、より多くのレコードを取得するか、次の位置を変更します。|  
|**adIndex**|0x100000|インデックスの名前を指定する[index](../../../ado/reference/ado-api/index-property.md)プロパティをサポートしています。|  
|**adMovePrevious**|0x200|は、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)および[MovePrevious](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッドをサポートします。また、ブックマークを必要とせずに現在のレコードの位置を後方に移動するには、 [move](../../../ado/reference/ado-api/move-method-ado.md)メソッドまたは[GetRows](../../../ado/reference/ado-api/getrows-method-ado.md)メソッドを使用します。|  
|**adNotify**|0x40000|基になるデータプロバイダーが通知をサポートしていることを示します。これは、**レコードセット**イベントがサポートされるかどうかを決定します。|  
|**adResync**|0x20000|は、基になるデータベースで表示されているデータを使用してカーソルを更新するための再[同期](../../../ado/reference/ado-api/resync-method.md)メソッドをサポートしています。|  
|**adSeek**|0x200000|では、**レコードセット**内の行を検索する[Seek](../../../ado/reference/ado-api/seek-method.md)メソッドがサポートされています。|  
|**adUpdate**|0x1008000|では、既存のデータを変更するための[Update](../../../ado/reference/ado-api/update-method.md)メソッドがサポートされています。|  
|**adUpdateBatch**|0x10000|では、バッチ更新 ([UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)および[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)メソッド) をサポートして、変更のグループをプロバイダーに送信します。|  
  
## <a name="adowfc-equivalent"></a>同等の ADO/WFC  
 パッケージ: **com. ms. wfc. データ**  
  
|常時|  
|--------------|  
|AdoEnums を指定します。|  
|AdoEnums. APPROXPOSITION|  
|AdoEnums を指定します。|  
|AdoEnums を削除します。|  
|AdoEnums を参照してください。|  
|AdoEnums HOLDRECORDS|  
|AdoEnums を指定します。|  
|AdoEnums MOVEPREVIOUS|  
|AdoEnums を指定します。通知|  
|AdoEnums の再同期|  
|AdoEnums を検索します。|  
|AdoEnums を更新します。|  
|AdoEnums. UPDATEBATCH|  
  
## <a name="applies-to"></a>適用対象  
 [Supports メソッド](../../../ado/reference/ado-api/supports-method.md)
