---
title: データベースのメタデータを使用して |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 8b048371-e912-4ed1-afd7-436978f48888
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 0bad06da093edd83b7df2e1c10f2b68bdca7a210
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798667"
---
# <a name="using-database-metadata"></a>データベースのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

データベースのサポート内容に関する情報をクエリする用途向けに、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerDatabaseMetaData](../../connect/jdbc/reference/sqlserverdatabasemetadata-class.md) クラスが実装されています。 このクラスには、単一値形式または結果セットとして情報を返すメソッドが多数存在します。

SQLServerDatabaseMetaData オブジェクトを作成するには、[SQLServerConnection](../../connect/jdbc/reference/sqlserverconnection-class.md) クラスの [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverconnection.md) メソッドを使用して接続先のデータベースに関する情報を取得します。

次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース関数に渡される、SQLServerConnection クラスの getMetaData メソッドは、SQLServerDatabaseMetadata オブジェクトとのさまざまなメソッドを返すために使用しますSQLServerDatabaseMetaData オブジェクトを使用して、ドライバー、ドライバーのバージョン、データベース名、およびデータベースのバージョンに関する情報を表示します。

[!code[JDBC#UsingDBMetaData1](../../connect/jdbc/codesnippet/Java/using-database-metadata_1.java)]

## <a name="see-also"></a>参照

[JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
