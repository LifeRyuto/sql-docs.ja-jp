---
title: updateObject Method (java.lang.String, java.lang.Object) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.updateObject (java.lang.String, java.lang.Object)
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f6999d9c-eab6-4e4d-96d8-e0fa4b4b87e3
author: MightyPen
ms.author: genemi
ms.openlocfilehash: de499e4cc11f1da1780878e4c921d161ee8b2693
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67998446"
---
# <a name="updateobject-method-javalangstring-javalangobject"></a>updateObject (java.lang.String, java.lang.Object) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  渡された列名を使用して、指定された列を **Object** 値で更新します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void updateObject(java.lang.String columnName,  
                         java.lang.Object x)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *columnName*  
  
 列名を含む**文字列**です。  
  
 *obj*  
  
 **Object** 値。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 この updateObject メソッドは、java.sql.ResultSet インターフェイスの updateObject メソッドで規定されています。  
  
## <a name="see-also"></a>参照  
 [updateObject メソッド &#40;SQLServerResultSet&#41;](../../../connect/jdbc/reference/updateobject-method-sqlserverresultset.md)   
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
