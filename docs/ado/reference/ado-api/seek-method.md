---
title: Seek メソッド |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset21::Seek
- Recordset21::raw_Seek
helpviewer_keywords:
- Seek method [ADO]
ms.assetid: 129293d2-19d3-4940-bf64-483ee72fb4a1
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 89b82d6efe87cec6643d68837447ed64a6f69059
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63314703"
---
# <a name="seek-method"></a>Seek メソッド
インデックスを検索、 [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md)を指定した値と一致して、その行に現在の行位置を変更する行をすばやく検索します。  
  
## <a name="syntax"></a>構文  
  
```  
  
recordset.Seek KeyValues, SeekOption  
```  
  
#### <a name="parameters"></a>パラメーター  
 *KeyValues*  
 配列の**バリアント**値。 インデックスは 1 つまたは複数の列と、配列に対応する各列に対して比較する値が含まれています。  
  
 *SeekOption*  
 A [SeekEnum](../../../ado/reference/ado-api/seekenum.md)重視すると、インデックスの列と、対応する比較の種類を指定する値*KeyValues*します。  
  
## <a name="remarks"></a>コメント  
 使用して、**シーク**メソッドと組み合わせて、[インデックス](../../../ado/reference/ado-api/index-property.md)プロパティを基になるプロバイダーのインデックスをサポートしている場合、**レコード セット**オブジェクト。 使用、[サポート](../../../ado/reference/ado-api/supports-method.md)**(adSeek)** 基になるプロバイダーがサポートしているかどうかを判断するメソッド**シーク**、および**Supports(adIndex)** プロバイダーはインデックスをサポートするかどうかを判断するメソッドです。 (たとえば、 [OLE DB Provider for Microsoft Jet](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-microsoft-jet.md)サポート**シーク**と**インデックス**)。  
  
 場合**シーク**エラーは、目的の行は見つかりませんが発生して、行がの末尾に配置されている、 **Recordset**します。 設定、**インデックス**プロパティをこのメソッドを実行する前に目的のインデックス。  
  
 このメソッドは、サーバー側のカーソルでのみサポートされます。 シークはときにサポートされていません、 **Recordset**オブジェクトの[CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md)プロパティの値が**adUseClient**します。  
  
 このメソッドは、必ず際に使用される、**レコード セット**でオブジェクトが開かれた、 [CommandTypeEnum](../../../ado/reference/ado-api/commandtypeenum.md)の値**adCmdTableDirect**します。  
  
## <a name="applies-to"></a>適用対象  
 [Recordset オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>参照  
 [Seek メソッドおよび Index プロパティの例 (VB)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vb.md)   
 [Seek メソッドおよび Index プロパティの例 (vc++)](../../../ado/reference/ado-api/seek-method-and-index-property-example-vc.md)   
 [Find メソッド (ADO)](../../../ado/reference/ado-api/find-method-ado.md)   
 [Index プロパティ](../../../ado/reference/ado-api/index-property.md)
