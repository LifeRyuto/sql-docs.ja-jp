---
title: データ ファイルとフォーマット ファイルを使用して |マイクロソフトのドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- bulk copy [ODBC], file formats
- ODBC, functions
- SQL Server Native Client ODBC driver, bulk copy
- bulk copy [SQL Server Native Client]
- ODBC, bulk copy operations
- bulk copy [ODBC], data files
ms.assetid: c01b7155-3f0a-473d-90b7-87a97bc56ca5
author: MightyPen
ms.author: genemi
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: f4c377bbfbe4170b5631ba1ac9c017af1176b279
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63013980"
---
# <a name="using-data-files-and-format-files"></a>データ ファイルとフォーマット ファイルの使用
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
[!INCLUDE[SNAC_Deprecated](../../includes/snac-deprecated.md)]

  最も単純な一括コピー プログラムでは次の操作を実行します。  
  
1.  呼び出し[bcp_init](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-init.md)を指定するテーブルからの一括コピー出力 (BCP_OUT を設定する) またはデータ ファイルを表示します。  
  
2.  呼び出し[bcp_exec](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)一括コピー操作を実行します。  
  
 データ ファイルはネイティブ モードで作成されるので、テーブルやビューのすべての列から取得したデータは、データベースと同じ形式でデータ ファイルに格納されます。 その後、同様の手順を使用して、このデータ ファイルをサーバーに一括コピーできます。ただし、DB_OUT ではなく DB_IN を設定します。 この操作は、コピー元のテーブルとコピー先のテーブルの構造が厳密に同じ場合にのみ機能します。 結果として得られるデータ ファイルできますへの入力としても、 **bcp**ユーティリティを使用して、 **/n** (ネイティブ モード) スイッチ。  
  
 テーブルやビューから直接取得するのではなく、[!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの結果セットを一括コピー出力するには、次の操作を実行します。  
  
1.  呼び出す**bcp_init**一括コピーを指定する、出力が、テーブル名に NULL を指定します。  
  
2.  呼び出す[bcp_control](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)で*eOption*に BCPHINTS を設定し、 *iValue* TRANSACT-SQL ステートメントを含む SQLTCHAR 文字列へのポインターに設定します。  
  
3.  呼び出す**bcp_exec**一括コピー操作を実行します。  
  
 結果セットを生成するステートメントであればどのような [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントも使用できます。 作成されるデータ ファイルには [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントの最初の結果セットが格納されます。 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで複数の結果セットが生成される場合、一括コピーでは、最初の結果セットよりも後にある結果セットは無視されます。  
  
 も、テーブル内の別の形式でデータを格納する列のデータ ファイルを作成するには[bcp_columns](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-columns.md)列数は変更を指定する、呼び出す[bcp_colfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-colfmt.md)各列の形式変更するには。 これは、呼び出した後**bcp_init**呼び出す前に**bcp_exec**します。 **bcp_colfmt**列のデータがデータ ファイルに格納されている形式を指定します。 これは、一括コピー入力または出力するときに使用できます。使用することも**bcp_colfmt**行と列のターミネータを設定します。 たとえば、データにタブ文字が含まれていない場合を作成、タブ区切りファイルを使用して**bcp_colfmt**として各列のターミネータがタブ文字を設定します。  
  
 ときに一括コピー出力を使用して**bcp_colfmt**、簡単に呼び出すことで作成したデータ ファイルを記述したフォーマット ファイルを作成することができます[bcp_writefmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-writefmt.md)を最後に呼び出した後**bcp_colfmt**.  
  
 一括コピー フォーマット ファイルで説明されているデータ ファイルから、呼び出すことによって、フォーマット ファイルを読み取る[bcp_readfmt](../../relational-databases/native-client-odbc-extensions-bulk-copy-functions/bcp-readfmt.md)後**bcp_init**する前に**bcp_exec**します。  
  
 **Bcp_control**関数への一括コピー時にいくつかのオプションを制御する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ ファイルから。 **bcp_control**エラーの終了前に、一括コピー、停止、行、およびバッチ サイズを開始するファイルの行の最大数などのオプションを設定します。  
  
## <a name="see-also"></a>参照  
 [一括コピー操作を実行する&#40;ODBC&#41;](../../relational-databases/native-client-odbc-bulk-copy-operations/performing-bulk-copy-operations-odbc.md)  
  
  
