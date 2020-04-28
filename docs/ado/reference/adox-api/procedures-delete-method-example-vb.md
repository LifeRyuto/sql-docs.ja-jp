---
title: Procedures Delete メソッドの例 (VB) |Microsoft Docs
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
- Delete method [ADOX], Visual Basic example
ms.assetid: 94f1ac93-e778-4a40-a85e-94bce5316ac7
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f5c7dfc901434c086b46bfb11c70e1eb2ee3bff7
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "67965367"
---
# <a name="procedures-delete-method-example-vb"></a>Procedures Delete メソッドの例 (VB)
次のコード[は、プロシージャコレクションの](../../../ado/reference/adox-api/procedures-collection-adox.md) [delete](../../../ado/reference/adox-api/delete-method-adox-collections.md)メソッドを使用してプロシージャを削除する方法を示しています。  
  
```  
' BeginDeleteProcedureVB  
Sub Main()  
    On Error GoTo DeleteProcedureError  
  
    Dim cat As New ADOX.Catalog  
  
    ' Open the catalog.  
    cat.ActiveConnection = _  
        "Provider='Microsoft.Jet.OLEDB.4.0';" & _  
        "Data Source='Northwind.mdb';"  
  
    ' Delete the procedure.  
    cat.Procedures.Delete "CustomerById"  
  
    'Clean up.  
    Set cat.ActiveConnection = Nothing  
    Set cat = Nothing  
    Exit Sub  
  
DeleteProcedureError:  
    Set cat = Nothing  
  
    If Err <> 0 Then  
        MsgBox Err.Source & "-->" & Err.Description, , "Error"  
    End If  
End Sub  
' EndDeleteProcedureVB  
```  
  
## <a name="see-also"></a>参照  
 [ActiveConnection プロパティ (ADOX)](../../../ado/reference/adox-api/activeconnection-property-adox.md)   
 [Catalog オブジェクト (ADOX)](../../../ado/reference/adox-api/catalog-object-adox.md)   
 [Delete メソッド (ADOX Collections)](../../../ado/reference/adox-api/delete-method-adox-collections.md)   
 [プロシージャオブジェクト (ADOX)](../../../ado/reference/adox-api/procedure-object-adox.md)   
 [Procedures コレクション (ADOX)](../../../ado/reference/adox-api/procedures-collection-adox.md)
