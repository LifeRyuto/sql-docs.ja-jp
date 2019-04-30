---
title: CancelBatch メソッド (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_CancelBatch
- Recordset15::CancelBatch
helpviewer_keywords:
- CancelBatch method [ADO]
ms.assetid: dbdc2574-e44e-4d95-b03d-4a5d9e9adf3c
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c8f0268a91b66f6f26eec1d87502355a1c9795a
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63239788"
---
# <a name="cancelbatch-method-ado"></a>CancelBatch メソッド (ADO)
保留中のバッチ更新をキャンセルします。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.CancelBatchAffectRecords  
```  
  
#### <a name="parameters"></a>パラメーター  
 *AffectRecords*  
 任意。 [AffectEnum](../../../ado/reference/ado-api/affectenum.md)レコードの数を示す値、 **CancelBatch**メソッドに影響されます。  
  
## <a name="remarks"></a>コメント  
 使用して、 **CancelBatch**保留中の更新プログラムをキャンセルするメソッド、[レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)バッチ更新モードでします。 場合、**レコード セット**が即時更新モードで呼び出す**CancelBatch**せず**adAffectCurrent**エラーが生成されます。  
  
 現在のレコードを編集して、呼び出すときに、新しいレコードを追加するか**CancelBatch**、ADO を最初に呼び出す、 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)キャッシュされた変更をキャンセルするメソッド。 保留中のすべての変更、その後、 **Recordset**は取り消されます。  
  
 現在のレコードを後で確定できない可能性があります、 **CancelBatch**呼び出すには中、新しいレコードを追加した場合に特にです。 このためがの既知の場所に現在のレコードの位置を設定することをお勧め、**レコード セット**後、 **CancelBatch**呼び出します。 たとえば、呼び出し、 [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md)メソッド。  
  
 プロバイダーは警告を返します (たとえば、レコードが別のユーザーによって削除されている場合) の基になるデータの競合があるため、保留中の更新をキャンセルの試行に失敗した場合、[エラー](../../../ado/reference/ado-api/errors-collection-ado.md)コレクションは停止されませんが、プログラムの実行。 要求されたすべてのレコードの競合がある場合にのみ、実行時エラーが発生します。 使用して、[フィルター](../../../ado/reference/ado-api/filter-property.md)プロパティ (**adFilterAffectedRecords**) および[状態](../../../ado/reference/ado-api/status-property-ado-recordset.md)が競合しているレコードを検索するプロパティ。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [UpdateBatch および CancelBatch メソッドの例 (VB)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vb.md)   
 [UpdateBatch および CancelBatch メソッドの例 (vc++)](../../../ado/reference/ado-api/updatebatch-and-cancelbatch-methods-example-vc.md)   
 [Cancel メソッド (ADO)](../../../ado/reference/ado-api/cancel-method-ado.md)   
 [Cancel メソッド (RDS)](../../../ado/reference/rds-api/cancel-method-rds.md)   
 [CancelUpdate メソッド (ADO)](../../../ado/reference/ado-api/cancelupdate-method-ado.md)   
 [CancelUpdate メソッド (RDS)](../../../ado/reference/rds-api/cancelupdate-method-rds.md)   
 [Clear メソッド (ADO)](../../../ado/reference/ado-api/clear-method-ado.md)   
 [LockType プロパティ (ADO)](../../../ado/reference/ado-api/locktype-property-ado.md)   
 [UpdateBatch メソッド](../../../ado/reference/ado-api/updatebatch-method.md)
