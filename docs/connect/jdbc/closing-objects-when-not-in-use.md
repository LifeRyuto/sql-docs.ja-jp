---
title: 使用されていないときにオブジェクトを閉じる |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: ce8f9b35-c761-4b0c-9a46-985eef2c2e0b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b2a9539599848f86a84cd03838c1fa7412c24fb1
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67957306"
---
# <a name="closing-objects-when-not-in-use"></a>使用されていないオブジェクトを閉じる
[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

  [!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] のオブジェクト、特に [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)、または Statement オブジェクト ([SQLServerStatement](../../connect/jdbc/reference/sqlserverstatement-class.md)、[SQLServerPreparedStatement](../../connect/jdbc/reference/sqlserverpreparedstatement-class.md)、[SQLServerCallableStatement](../../connect/jdbc/reference/sqlservercallablestatement-class.md) など) の 1 つを使用する場合、必要でなくなったときは close メソッドを使用して明示的に閉じる必要があります。 これにより、Java 仮想マシンのガベージ コレクターによる処理を待たずに、迅速にドライバーとサーバーのリソースを解放できるため、パフォーマンスが向上します。  
  
 スクロール ロックを使用しているときに、サーバー上で適切なコンカレンシーを維持するためには、オブジェクトを閉じることが特に重要となります。 最後にアクセスしたフェッチ バッファーのスクロール ロックは、結果セットが閉じられるまで保持されます。 同様に、ステートメントの準備されたハンドルは、ステートメントが閉じられるまで保持されます。 複数のステートメントで接続を再利用する場合は、スコープから出る前にステートメントを閉じることで、サーバーが準備されたハンドルを早期にクリーンアップできるようになります。  
  
## <a name="see-also"></a>参照  
 [JDBC ドライバーによるパフォーマンスと信頼性の強化](../../connect/jdbc/improving-performance-and-reliability-with-the-jdbc-driver.md)  
  
  
