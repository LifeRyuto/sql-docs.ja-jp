---
title: FilterGroupEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- FilterGroupEnum
helpviewer_keywords:
- FilterGroupEnum enumeration [ADO]
ms.assetid: b22e725e-84bd-4286-a070-290c278c3783
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: db586609b90ba023e2a1700642cb678e8f08a8b2
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66694894"
---
# <a name="filtergroupenum"></a>FilterGroupEnum
フィルター処理するレコードのグループを指定します、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adFilterAffectedRecords**|2|最後に影響を受けるレコードのみを表示するためのフィルター[削除](../../../ado/reference/ado-api/delete-method-ado-recordset.md)、[再同期](../../../ado/reference/ado-api/resync-method.md)、 [UpdateBatch](../../../ado/reference/ado-api/updatebatch-method.md)、または[CancelBatch](../../../ado/reference/ado-api/cancelbatch-method-ado.md)呼び出します。|  
|**adFilterConflictingRecords**|5|最後のバッチ更新が失敗したレコードを表示するためのフィルター。|  
|**adFilterFetchedRecords**|3|現在のキャッシュ内のレコードを表示するためのフィルター-つまり、データベースからレコードを取得するには、最後の呼び出しの結果。|  
|**adFilterNone**|0|現在のフィルターを削除し、表示するためのすべてのレコードを復元します。|  
|**adFilterPendingRecords**|1|変更されたが、サーバーにまだ送信されていないレコードだけを表示するためのフィルター。 バッチ更新モードにのみ適用できます。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.FilterGroup.AFFECTEDRECORDS|  
|AdoEnums.FilterGroup.CONFLICTINGRECORDS|  
|AdoEnums.FilterGroup.FETCHEDRECORDS|  
|AdoEnums.FilterGroup.NONE|  
|AdoEnums.FilterGroup.PENDINGRECORDS|  
  
## <a name="applies-to"></a>適用対象  
 [Filter プロパティ](../../../ado/reference/ado-api/filter-property.md)
