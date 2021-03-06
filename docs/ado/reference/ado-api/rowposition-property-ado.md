---
title: RowPosition プロパティ (ADO) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- ADORecordConstruction::put_RowPosition
- ADORecordConstruction::PutRowPosition
- ADORecordConstruction::GetRowPosition
- ADORecordConstruction::RowPosition
- ADORecordConstruction::get_RowPosition
helpviewer_keywords:
- RowPosition property [ADO]
ms.assetid: 9d068fed-39bf-4842-afc3-686a2af2145d
author: MightyPen
ms.author: genemi
ms.openlocfilehash: a333a2be2728f3c0b412246b0a793dae64096ae5
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67931227"
---
# <a name="rowposition-property-ado"></a>RowPosition プロパティ (ADO)
**ADORecordsetConstruction**オブジェクトからの OLE DB **rowposition**オブジェクトを取得します。値の設定もできます。 **Put_RowPosition**を使用して**rowposition**オブジェクトを設定すると、結果として得られる**レコードセット**オブジェクトは**rowposition**オブジェクトを使用して現在の行を決定します。  
  
 読み取りと書き込みが可能です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT get_RowPosition([out, retval] IUnknown** ppRowPos);  
HRESULT put_RowPosition([in] IUnknown* pRowPos);  
```  
  
## <a name="parameters"></a>パラメーター  
 *ppRowPos*  
 OLE DB **Rowposition**オブジェクトへのポインター。  
  
 *PRowPos*  
 OLE DB **Rowposition**オブジェクト。  
  
## <a name="return-values"></a>戻り値  
 このプロパティメソッドは、S_OK および E_FAIL を含む標準の HRESULT 値を返します。  
  
## <a name="remarks"></a>解説  
 このプロパティが設定されている場合、 **Rowposition**オブジェクトの**Rowset**オブジェクトが**Recordset**オブジェクトの**rowset**オブジェクトと異なる場合、前者は後者よりも優先されます。 同じ動作が、 **Rowposition**の現在の**チャプター**にも適用されます。  
  
## <a name="applies-to"></a>適用対象  
 [ADORecordsetConstruction インターフェイス](../../../ado/reference/ado-api/adorecordsetconstruction-interface.md)
