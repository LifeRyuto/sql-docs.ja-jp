---
title: Status プロパティの例 (Field) (VB) |Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
dev_langs:
- VB
helpviewer_keywords:
- Status property [ADO Field], Visual Basic example
ms.assetid: fdd09b60-39c7-44be-8008-e891a031f80e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: caf016190e585aa64ee24f81fdcc0c18a4dab93f
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63027591"
---
# <a name="status-property-example-field-vb"></a>Status プロパティの例 (Field) (VB)
次の例を使用して読み取り/書き込みフォルダーからドキュメントを開くと、[インターネット パブリッシング用プロバイダー](../../../ado/guide/appendixes/microsoft-ole-db-provider-for-internet-publishing.md)します。 [状態](../../../ado/reference/ado-api/status-property-ado-field.md)のプロパティを[フィールド](../../../ado/reference/ado-api/field-object.md)のオブジェクト、[レコード](../../../ado/reference/ado-api/record-object-ado.md)は最初に設定されます**adFieldPendingInsert**に更新します。**adfieldok で**します。  
  
```  
'BeginStatusFieldVB  
  
 ' to integrate this code replace the values in the source string  
  
Sub Main()  
  
   Dim File As ADODB.Record  
   Dim strFile As String  
   Dim Cnxn As ADODB.Connection  
   Dim strCnxn As String  
  
   Set Cnxn = New ADODB.Connection  
   strCnxn = "url=https://MyServer/"  
   Cnxn.Open strCnxn  
  
   Set File = New ADODB.Record  
   strFile = "Folder/FileName"  
   ' Open a read/write document  
   File.Source = strFile  
   File.ActiveConnection = Cnxn  
   File.Mode = adModeReadWrite  
   File.Open  
  
   Debug.Print "Append a couple of fields"  
  
   File.Fields.Append "chektest:fld1", adWChar, 42, adFldUpdatable, "fld1"  
   File.Fields.Append "chektest:fld2", adWChar, 42, adFldUpdatable, "fld2"  
  
   Debug.Print "status for the fields"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert  
  
    'turn off error-handling to verify field status  
   On Error Resume Next  
  
   File.Fields.Update  
  
   Debug.Print "Update succeeds"  
   Debug.Print File.Fields("chektest:fld1").Status 'adfldpendinginsert + adFieldUnavailable  
   Debug.Print File.Fields("chektest:fld2").Status 'adfldpendinginsert + adFieldUnavailable  
  
    ' resume default error-handling  
   On Error GoTo 0  
  
     ' clean up  
    File.Close  
    Cnxn.Close  
    Set File = Nothing  
    Set Cnxn = Nothing  
  
End Sub  
'EndStatusFieldVB  
```  
  
 次の例では、既知の削除**フィールド**から、**レコード**からドキュメントを開きます。 **状態**プロパティが最初に設定する**adfieldok で**、し**adFieldPendingUnknown**します。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
 次のコードの削除、**フィールド**から、**レコード**読み取り専用のドキュメントを開きます。 **ステータス**に設定されます**adFieldPendingDelete**します。 [Update](../../../ado/reference/ado-api/update-method.md)、削除は失敗と**状態**なります**adFieldPendingDelete** plus **adFieldPermissionDenied**します。 [CancelUpdate](../../../ado/reference/ado-api/cancelupdate-method-ado.md)クリア、保留中**状態**設定します。  
  
```  
Attribute VB_Name = "StatusField"  
```  
  
## <a name="see-also"></a>参照  
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [Record オブジェクト (ADO)](../../../ado/reference/ado-api/record-object-ado.md)   
 [Status プロパティ (ADO Field)](../../../ado/reference/ado-api/status-property-ado-field.md)
