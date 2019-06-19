---
title: CursorLocationEnum |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- CursorLocationEnum
helpviewer_keywords:
- CursorLocationEnum enumeration [ADO]
ms.assetid: acb255ff-1734-4b70-89bb-aef862b4c63b
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 43c2043917d6b21293fea71566dfdf1202b6f59e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66695653"
---
# <a name="cursorlocationenum"></a>CursorLocationEnum
カーソル サービスの場所を指定します。  
  
|定数|値|説明|  
|--------------|-----------|-----------------|  
|**adUseClient**|3|ローカル カーソル ライブラリによって提供されたクライアント側のカーソルを使用します。 ローカル カーソル サービス多くの場合は、ドライバーによって提供されるカーソルよりも多くの機能が有効にする機能に関する利点を提供可能性がありますこの設定を使用できます。 旧バージョンと互換性のため、シノニム**adUseClientBatch**もサポートされています。|  
|**adUseNone**|1|カーソルのサービスを使用しません。 (この定数は廃止は、旧バージョンと互換性のためにのみ表示されます)。|  
|**adUseServer**|2|既定値です。 データ プロバイダーまたはドライバーによって提供されたカーソルを使用します。 これらのカーソルでは、非常に柔軟性がありますし、他のユーザー データ ソースへの変更を検出できるようにします。 ただし、一部の機能、 [for OLE DB の Microsoft カーソル サービス](../../../ado/guide/data/the-microsoft-cursor-service-for-ole-db.md)関連付けを解除など、<br /><br /> [レコード セット](../../../ado/reference/ado-api/recordset-object-ado.md)オブジェクト、サーバー側カーソルをシミュレートできませんし、これらの機能はこの設定では使用できません。|  
  
## <a name="adowfc-equivalent"></a>ADO と WFC と同等  
 パッケージ: **com.ms.wfc.data**  
  
|定数|  
|--------------|  
|AdoEnums.CursorLocation.CLIENT|  
|AdoEnums.CursorLocation.NONE|  
|AdoEnums.CursorLocation.SERVER|  
  
## <a name="applies-to"></a>適用対象  
 [CursorLocation プロパティ (ADO)](../../../ado/reference/ado-api/cursorlocation-property-ado.md)
