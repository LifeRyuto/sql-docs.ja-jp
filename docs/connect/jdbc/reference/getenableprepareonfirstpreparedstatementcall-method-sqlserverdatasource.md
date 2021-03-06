---
title: getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2018
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ''
author: MightyPen
ms.author: genemi
ms.openlocfilehash: ce67d0e688ae3ad8909915d9906608f5370830b1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67983392"
---
# <a name="getenableprepareonfirstpreparedstatementcall-method-sqlserverdatasource"></a>getEnablePrepareOnFirstPreparedStatementCall メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  **EnablePrepareOnFirstPreparedStatementCall** connection プロパティの値を返します。 この構成が false を返す場合、準備されたステートメントの最初の実行では sp_executesql が呼び出され、ステートメントは準備されません。2回目の実行が行われると、sp_prepexec が呼び出され、実際には準備されたステートメントハンドルが設定されます。 次の実行では、sp_execute を呼び出します。 これにより、ステートメントが1回だけ実行された場合に、準備されたステートメントを閉じる必要がなくなります。 
  
## <a name="syntax"></a>構文  
  
```
public boolean getEnablePrepareOnFirstPreparedStatementCall();  
```  
  
## <a name="return-value"></a>戻り値  
 **EnablePrepareOnFirstPreparedStatementCall** connection プロパティの**ブール**値を返します。  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
 
## <a name="remarks"></a>Remarks  
 このメソッドは、JDBC driver バージョン6.4 以降で使用できます。
 
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
