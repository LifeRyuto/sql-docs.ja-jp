---
title: ActualSize および DefinedSize プロパティの例 (VB) |Microsoft Docs
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
- DefinedSize property [ADO], Visual Basic example
- ActualSize property [ADO], Visual Basic example
ms.assetid: bff2c273-b535-4b32-83b3-0336a406859c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: b8edd574dea39712f8b2acbc092a0a90482d2fff
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66698918"
---
# <a name="actualsize-and-definedsize-properties-example-vb"></a>ActualSize および DefinedSize プロパティの例 (VB)
この例では、 [ActualSize](../../../ado/reference/ado-api/actualsize-property-ado.md)と[DefinedSize](../../../ado/reference/ado-api/definedsize-property.md)定義されたサイズと、フィールドの実際のサイズを表示するプロパティ。  
  
```  
'BeginActualSizeVB  
  
    'To integrate this code  
    'replace the data source and initial catalog values  
    'in the connection string  
  
Public Sub Main()  
    On Error GoTo ErrorHandler  
  
    'recordset and connection variables  
    Dim rstStores As ADODB.Recordset  
    Dim SQLStores As String  
    Dim strCnxn As String  
     'record variables  
    Dim strMessage As String  
  
    ' Open a recordset for the Stores table  
    strCnxn = "Provider='sqloledb';Data Source='MySqlServer';" & _  
        "Initial Catalog='Northwind';Integrated Security='SSPI';"  
    Set rstStores = New ADODB.Recordset  
  
    SQLStores = "Suppliers"  
    rstStores.Open SQLStores, strCnxn, adOpenForwardOnly, adLockReadOnly, adCmdTable  
    'the above two lines of code are identical as the default values for  
    'CursorType and LockType arguments match those indicated  
  
    ' Loop through the recordset displaying the contents  
    ' of the store_name field, the field's defined size,  
    ' and its actual size.  
    rstStores.MoveFirst  
  
    Do Until rstStores.EOF  
        strMessage = "Company name: " & rstStores!CompanyName & _  
        vbCrLf & "Defined size: " & _  
        rstStores!CompanyName.DefinedSize & _  
        vbCrLf & "Actual size: " & _  
        rstStores!CompanyName.ActualSize & vbCrLf  
  
        MsgBox strMessage, vbOKCancel, "ADO ActualSize Property (Visual Basic)"  
        rstStores.MoveNext  
    Loop  
  
    ' clean up  
    rstStores.Close  
    Set rstStores = Nothing  
    Exit Sub  
  
ErrorHandler:  
    ' clean up  
    If Not rstStores Is Nothing Then  
        If rstStores.State = adStateOpen Then rstStores.Close  
    End If  
    Set rstStores = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
'EndActualSizeVB  
```  
  
## <a name="see-also"></a>関連項目  
 [ActualSize プロパティ (ADO)](../../../ado/reference/ado-api/actualsize-property-ado.md)   
 [DefinedSize プロパティ](../../../ado/reference/ado-api/definedsize-property.md)   
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)
