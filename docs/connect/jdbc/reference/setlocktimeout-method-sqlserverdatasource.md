---
title: setLockTimeout メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.setLockTimeout
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 10dca5aa-1851-4326-9ae9-7a8430d12d11
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 32f61572dca7124e552a9d40497a3385bc243b31
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66790473"
---
# <a name="setlocktimeout-method-sqlserverdatasource"></a>setLockTimeout メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  データベースがロック タイムアウトを通知するまでに待機する時間 (ミリ秒) を示す **int** 値を設定します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void setLockTimeout(int lockTimeout)  
```  
  
#### <a name="parameters"></a>パラメーター  
 *lockTimeout*  
  
 待機する時間 (ミリ秒) を含む **int** 値です。  
  
## <a name="remarks"></a>Remarks  
 ロック タイムアウトは、データベースがロック タイムアウトを通知するまでに待機する時間 (ミリ秒) です。既定値の -1 は、無制限に待機することを意味します。 値を指定した場合、接続上のすべてのステートメントに対する既定値になります。  
  
> [!NOTE]  
>  値 0 を指定した場合、待機が行われません。 lockTimeout プロパティが設定されていない場合、[getLockTimeout](../../../connect/jdbc/reference/getlocktimeout-method-sqlserverdatasource.md) メソッドは既定値の -1 を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
