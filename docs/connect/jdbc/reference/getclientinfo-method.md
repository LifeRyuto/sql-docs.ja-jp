---
title: getClientInfo () メソッド |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: b06a5ced-b760-4c78-b17e-854ce95a1a5c
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: bccb7e0cee039ad6591acf3805f2ba70c9c7655a
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66763828"
---
# <a name="getclientinfo-method-"></a>getClientInfo () メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  JDBC ドライバーでサポートされている、各クライアント情報のプロパティの名前と現在の値を含む一覧を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public java.util.Properties getClientInfo()  
```  
  
## <a name="return-value"></a>戻り値  
 ドライバーでサポートされている、各クライアント情報のプロパティの名前と現在の値を含む Properties オブジェクトです。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この getClientInfo メソッドは、java.sql.Connection インターフェイスの getClientInfo メソッドによって指定されます。  
  
 [!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] ではクライアント情報のプロパティをサポートしていません。 その結果、このメソッドは、空のプロパティ オブジェクトを返します。  
  
 同様に、アプリケーションでは、[SQLServerDatabaseMetaData](../../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) クラスの [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) メソッドを使用して、ドライバーがサポートするクライアント情報プロパティの一覧を取得できます。 [getClientInfoProperties](../../../connect/jdbc/reference/getclientinfoproperties-method-sqlserverdatabasemetadata.md) メソッドでは、空の結果セットが返されます。  
  
## <a name="see-also"></a>参照  
 [getClientInfo メソッド &#40;SQLServerConnection&#41;](../../../connect/jdbc/reference/getclientinfo-method-sqlserverconnection.md)   
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [SQLServerConnection クラス](../../../connect/jdbc/reference/sqlserverconnection-class.md)  
  
  
