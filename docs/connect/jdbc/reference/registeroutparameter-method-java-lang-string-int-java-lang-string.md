---
title: registerOutParameter メソッドの種類と名前を |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerCallableStatement.registerOutParameter
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: f962c912-2475-4e1f-a384-579be2d17f37
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 5c0fb7eb2f50aabb2bcc2a51085f0afdd94cf419
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66802087"
---
# <a name="registeroutparameter-method-javalangstring-int-javalangstring"></a>registerOutParameter (java.lang.String, int, java.lang.String) メソッド
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  指定された名前の OUT パラメーターを、渡された JDBC 型と型名に登録します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void registerOutParameter(java.lang.String s,  
                                 int n,  
                                 java.lang.String s1)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *s*  
  
 パラメーターの名前を含む**文字列**です。  
  
 *n*  
  
 JDBC の型コード java.sql.Types で定義されています。  
  
 *s1*  
  
 完全修飾 SQL 型名を含む**文字列**です。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 この registerOutParameter メソッドは、java.sql.CallableStatement インターフェイスの registerOutParameter メソッドによって指定されます。  
  
## <a name="see-also"></a>参照  
 [registerOutParameter メソッド &#40;SQLServerCallableStatement&#41;](../../../connect/jdbc/reference/registeroutparameter-method-sqlservercallablestatement.md)   
 [SQLServerCallableStatement のメンバー](../../../connect/jdbc/reference/sqlservercallablestatement-members.md)   
 [SQLServerCallableStatement クラス](../../../connect/jdbc/reference/sqlservercallablestatement-class.md)  
  
  
