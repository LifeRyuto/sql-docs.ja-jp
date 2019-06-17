---
title: 次のメソッド (SQLServerResultSet) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.next
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 60248447-6908-4036-a779-a501453cd553
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 8fcd3125f45622ddd167acf06ed91ccffb02a3b5
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66779525"
---
# <a name="next-method-sqlserverresultset"></a>next メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  カーソルを現在の位置から 1 行下に移動します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean next()  
```  
  
## <a name="return-value"></a>戻り値  
 **true**新しい現在の行が有効な場合。 **false**を処理する行がない場合。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>Remarks  
 next メソッドは、java.sql.ResultSet インターフェイスの next メソッドで規定されています。  
  
 結果セットのカーソルは、初期状態では先頭行よりも前にあります。 最初に next メソッドを呼び出すと先頭行が現在の行になり、2 回目に呼び出すと 2 番目の行が現在の行になります。  
  
 入力ストリームが現在の行に対して開いている場合、next メソッドを呼び出すとストリームが暗黙的に閉じます。 [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトの警告チェーンは、新しい行が読み取られるとクリアされます。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
