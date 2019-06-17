---
title: SQLServerConnection クラス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 937292a6-1525-423e-a2b2-a18fd34c2893
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a14627f54e1d297642cb2c555fb8427acb2da5a7
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66803092"
---
# <a name="sqlserverconnection-class"></a>SQLServerConnection クラス
[!INCLUDE[Driver_JDBC_Download](../../../includes/driver_jdbc_download.md)]

  [!INCLUDE[msCoName](../../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] データベースへの JDBC 接続を表します。  
  
 **パッケージ:** com.microsoft.sqlserver.jdbc  
  
 **実装:** [ISQLServerConnection](../../../connect/jdbc/reference/isqlserverconnection-interface.md)、java.io.Serializable  
  
## <a name="syntax"></a>構文  
  
```  
  
public class SQLServerConnection  
```  
  
## <a name="remarks"></a>Remarks  
 SQLServerConnection では、JDBC 接続プールがサポートされており、JDBC の物理接続または JDBC の論理接続のいずれかを使用できます。 SQLServerConnection は、それから作成されたすべてのステートメントのトランザクション制御を管理し、XAResource アダプター経由で管理される XA の分散トランザクションに参加できます。  
  
 SQLServerConnection では、準備されたステートメント ハンドルのプールを管理します。 ステートメントは 1 回だけ準備され、通常はパラメーターに対して異なるデータ値を指定し、何度も実行されます。 準備されたステートメントは、論理 (プール) 接続の終了後も維持されます。  
  
> [!NOTE]  
>  SQLServerConnection はスレッド セーフではありません。 ただし、単一の接続から作成された複数のステートメントは、同時スレッドで同時に処理することができます。  
  
 このクラスは、SQLServerConnection クラス、java.sql.connection インターフェイス、および ISQLServerConnection インターフェイスへのアンラッピングをサポートしています。 詳細については、次を参照してください。[ラッパーとインターフェイス](../../../connect/jdbc/wrappers-and-interfaces.md)します。  
  
## <a name="see-also"></a>参照  
 [SQLServerConnection のメンバー](../../../connect/jdbc/reference/sqlserverconnection-members.md)   
 [JDBC Driver API リファレンス](../../../connect/jdbc/reference/jdbc-driver-api-reference.md)  
  
  
