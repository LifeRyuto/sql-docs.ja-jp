---
title: close メソッド (SQLServerResultSet) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
apiname:
- SQLServerResultSet.close
apilocation:
- sqljdbc.jar
apitype: Assembly
ms.assetid: 8f3adf5b-874e-4cf2-b4ef-672dda42d77a
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e78dbb981938e9af2fbe894919368da17347941a
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "67955582"
---
# <a name="close-method-sqlserverresultset"></a>close メソッド (SQLServerResultSet)
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [SQLServerResultSet](../../../connect/jdbc/reference/sqlserverresultset-class.md) オブジェクトのデータベースと JDBC リソースを、オブジェクトが自動的に閉じるときに解放されるのを待機しないで直ちに解放します。  
  
## <a name="syntax"></a>構文  
  
```  
  
public void close()  
```  
  
## <a name="exceptions"></a>例外  
 [SQLServerException](../../../connect/jdbc/reference/sqlserverexception-class.md)  
  
## <a name="remarks"></a>解説  
 close メソッドは、java.sql.ResultSet インターフェイスの close メソッドで規定されています。  
  
 SQLServerResultSet オブジェクトは、生成元の [SQLServerStatement](../../../connect/jdbc/reference/sqlserverstatement-class.md) オブジェクトが閉じられたとき、再実行されたとき、または複数の結果のシーケンスから次の結果を取得するために使用されたときに、その SQLServerStatement オブジェクトによって自動的に閉じられます。 SQLServerResultSet オブジェクトは、ガベージ コレクションの際にも自動的に閉じられます。  
  
 順方向専用、読み取り専用の大きな結果セットを 1 つだけ生成するようなステートメントを実行する場合、必要な行は、返された結果セットのうち、先頭のいくつかの行だけであるケースが少なくありません。 このような場合は、関連するステートメント オブジェクトの [cancel](../../../connect/jdbc/reference/cancel-method-sqlserverstatement.md) メソッドを呼び出してから結果セットを閉じることによって、残りの不要な行を破棄するために必要な処理時間を最小限に抑えることが可能です。 この手法を用いるかどうかは、短縮できる処理時間と、実行の取り消しに伴って生じる、サーバーに対するラウンド トリップ時間とのトレードオフを考慮したうえで判断することをお勧めします。  
  
## <a name="see-also"></a>参照  
 [SQLServerResultSet のメンバー](../../../connect/jdbc/reference/sqlserverresultset-members.md)   
 [SQLServerResultSet クラス](../../../connect/jdbc/reference/sqlserverresultset-class.md)  
  
  
