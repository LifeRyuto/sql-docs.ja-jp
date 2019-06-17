---
title: 結果を使用してメタデータを設定 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
ms.assetid: 5e37529a-30db-48c8-b90a-ae9657d0f6b0
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 60b854cc260f0488f56e77fb10a34025c80d7620
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: MTE75
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66798636"
---
# <a name="using-result-set-metadata"></a>結果セットのメタデータの使用

[!INCLUDE[Driver_JDBC_Download](../../includes/driver_jdbc_download.md)]

結果セットに格納されている列の情報をクエリするために、[!INCLUDE[jdbcNoVersion](../../includes/jdbcnoversion_md.md)] には、[SQLServerResultSetMetaData](../../connect/jdbc/reference/sqlserverresultsetmetadata-class.md) クラスが実装されています。 このクラスには、単一値の形式で情報を返すメソッドが多数存在します。

SQLServerResultSetMetaData オブジェクトを作成するには、使用することができます、 [getMetaData](../../connect/jdbc/reference/getmetadata-method-sqlserverresultset.md)のメソッド、 [SQLServerResultSet](../../connect/jdbc/reference/sqlserverresultset-class.md)クラス。

次の例では、開いている接続を[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal_md.md)]サンプル データベース関数に渡される、SQLServerResultSet クラスの getMetaData メソッドは、SQLServerResultSetMetaData オブジェクトとのさまざまなメソッドを返すために使用しますSQLServerResultSetMetaData オブジェクトを使用して、結果セットに含まれる列の名前とデータ型に関する情報を表示します。

[!code[JDBC#UsingResultSetMetaData1](../../connect/jdbc/codesnippet/Java/using-result-set-metadata_1.java)]

## <a name="see-also"></a>参照

[JDBC ドライバーによるメタデータの処理](../../connect/jdbc/handling-metadata-with-the-jdbc-driver.md)
