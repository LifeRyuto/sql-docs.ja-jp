---
title: getXopenStates メソッド (SQLServerDataSource) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerDataSource.getXopenStates
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: de6fdf6b-8345-4490-b35e-7115b61e782e
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c0a3859c3195d14243ff570493d3ae04c72d0780
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66768806"
---
# <a name="getxopenstates-method-sqlserverdatasource"></a>getXopenStates メソッド (SQLServerDataSource)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  XOPEN 互換の状態への SQL 状態の変換が有効になっているかどうかを示す **boolean** 値を返します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public boolean getXopenStates()  
```  
  
## <a name="return-value"></a>戻り値  
 XOPEN 互換の状態への SQL 状態の変換が有効になっている場合は **true** です。 それ以外の場合は、 **false**です。  
  
## <a name="remarks"></a>Remarks  
 xopenStates プロパティが **true** に設定されている場合、[!INCLUDE[jdbcNoVersion](../../../includes/jdbcnoversion_md.md)] は SQL 状態を XOPEN 互換の状態に変換します。 既定値は **false** です。この場合、JDBC ドライバーは SQL 99 の状態コードを生成します。 xopenStates が設定されていない場合、getXopenStates メソッドは既定値の **false** を返します。  
  
## <a name="see-also"></a>参照  
 [SQLServerDataSource のメンバー](../../../connect/jdbc/reference/sqlserverdatasource-members.md)   
 [SQLServerDataSource クラス](../../../connect/jdbc/reference/sqlserverdatasource-class.md)  
  
  
