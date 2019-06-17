---
title: getResponseBuffering メソッド (SQLServerStatement) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerStatement.getResponseBuffering()
apilocation:
- SQLServerStatement.getResponseBuffering()
apitype: Assembly
ms.assetid: a9a9ffdd-7ce3-4e0a-907c-34d6a54e6865
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 9c0d96ded45fe1b6cb68eda222039e01901ebc65
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66801328"
---
# <a name="getresponsebuffering-method-sqlserverstatement"></a>getResponseBuffering メソッド (SQLServerStatement)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトの応答バッファリング モードを取得します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public final java.lang.String getResponseBuffering()  
```  
  
## <a name="return-value"></a>戻り値  
 A**文字列**小文字を含む**完全**または**アダプティブ**します。  
  
## <a name="remarks"></a>Remarks  
 **adaptive** 値は、必要に応じて最小限のデータをバッファリングすることを示します。  
  
 **full** は、実行時にサーバーから結果全体を読み取ることを示します。  
  
 **アダプティブ**は JDBC Driver version 2.0 および 3.0 での既定値です。 **完全な**JDBC Driver version 2.0 よりも前の既定のでした。  
  
 詳細については、応答バッファリング モードを使用して、次を参照してください。[アダプティブ バッファリングを使用して](../../../connect/jdbc/using-adaptive-buffering.md)します。  
  
## <a name="see-also"></a>参照  
 [setResponseBuffering メソッド &#40;SQLServerStatement&#41;](../../../connect/jdbc/reference/setresponsebuffering-method-sqlserverstatement.md)   
 [SQLServerStatement のメンバー](../../../connect/jdbc/reference/sqlserverstatement-members.md)   
 [SQLServerStatement クラス](../../../connect/jdbc/reference/sqlserverstatement-class.md)  
  
  
