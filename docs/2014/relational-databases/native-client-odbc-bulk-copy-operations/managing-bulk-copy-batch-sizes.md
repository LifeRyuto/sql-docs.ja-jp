---
title: 一括コピーバッチサイズの管理 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: native-client
ms.topic: reference
helpviewer_keywords:
- SQL Server Native Client ODBC driver, bulk copy
- ODBC, bulk copy operations
- batches [ODBC]
- bulk copy [ODBC], batch sizes
ms.assetid: 4b24139f-788b-45a6-86dc-ae835435d737
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 07f87bf0f231419e4f1345369211ba6ceebf1d12
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63199174"
---
# <a name="managing-bulk-copy-batch-sizes"></a>一括コピー バッチ サイズの管理
  一括コピー操作でバッチを使用する主な目的は、トランザクションのスコープを定義することです。 一括コピー関数では、バッチ サイズが設定されていないと、一括コピー全体を 1 つのトランザクションと見なします。 バッチ サイズが設定されている場合、各バッチはそのバッチの終了時にコミットされるトランザクションで構成されます。  
  
 バッチ サイズを指定せずに一括コピーを実行し、エラーが発生した場合は、一括コピー全体がロールバックされます。 実行時間が長い一括コピーの復旧には時間がかかることがあります。 バッチ サイズを設定すると、各バッチが 1 つのトランザクションと見なされ、各バッチがコミットされます。 エラーが発生した場合は、最後の未解決のバッチだけがロールバックされます。  
  
 バッチ サイズは、ロックのオーバーヘッドにも影響を与えることがあります。 に対して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一括コピーを実行する場合は、 [bcp_control](../native-client-odbc-extensions-bulk-copy-functions/bcp-control.md)を使用して TABLOCK ヒントを指定し、行ロックではなくテーブルロックを取得できます。 1 つのテーブル ロックを設定すると、一括コピー操作全体のオーバーヘッドを最小限に抑えることができます。 TABLOCK を指定しないと各行がロックされるので、一括コピーの実行中にすべてのロックを保持するオーバーヘッドにより、パフォーマンスが低下することがあります。 トランザクションの長さだけロックが保持されるので、バッチ サイズを指定すると、定期的にコミットが発生して、その時点で保持されているロックが解放されるため、この問題を解決できます。  
  
 大量の行を一括コピーする場合、1 つのバッチを構成する行数がパフォーマンスに大きな影響を与えることがあります。 推奨バッチ サイズは、実行する一括コピーの種類によって異なります。  
  
-   
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] への一括コピーを行う場合は、TABLOCK 一括コピー ヒントを指定し、大きなバッチ サイズを設定します。  
  
-   TABLOCK を指定しない場合は、バッチ サイズを 1,000 行未満に制限します。  
  
 データファイルから一括コピーする場合は、 [bcp_exec](../native-client-odbc-extensions-bulk-copy-functions/bcp-exec.md)を呼び出す前に、bcpbatch オプションを指定して**bcp_control**を呼び出すことによってバッチサイズを指定します。 [Bcp_bind](../native-client-odbc-extensions-bulk-copy-functions/bcp-bind.md)と[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md)を使用してプログラム変数から一括コピーを行う場合、バッチサイズは[bcp_sendrow](../native-client-odbc-extensions-bulk-copy-functions/bcp-sendrow.md) *x*回を呼び出した後[bcp_batch](../native-client-odbc-extensions-bulk-copy-functions/bcp-batch.md)を呼び出すことによって制御されます。ここで、 *x*はバッチ内の行数です。  
  
 バッチはトランザクションのサイズを指定するだけでなく、ネットワーク経由でサーバーに行を送信するときにも影響を与えます。 一括コピー関数は、通常、ネットワークパケットがいっぱいになるまで**bcp_sendrow**から行をキャッシュしてから、完全なパケットをサーバーに送信します。 ただし、アプリケーションが**bcp_batch**を呼び出すと、そのパケットがいっぱいになっているかどうかに関係なく、現在のパケットがサーバーに送信されます。 バッチ サイズを非常に小さくすると、いっぱいになっていないパケットが大量にサーバーに送信されるので、パフォーマンスが低下することがあります。 たとえば、すべての**bcp_sendrow**の後に**bcp_batch**を呼び出すと、各行が個別のパケットで送信され、行が非常に大きい場合を除き、各パケットの領域が無駄になります。 SQL Server のネットワークパケットの既定のサイズは 4 KB ですが、アプリケーションでは、SQL_ATTR_PACKET_SIZE 属性を指定して[SQLSetConnectAttr](../native-client-odbc-api/sqlsetconnectattr.md)を呼び出すことによってサイズを変更できます。  
  
 バッチのもう1つの副作用は、 **bcp_batch**で完了するまで、各バッチが未処理の結果セットと見なされることです。 バッチが未処理のときに接続ハンドルで他の操作が試行された[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]場合、NATIVE Client ODBC ドライバーでは、SQLState = "HY000" およびエラーメッセージ文字列の次のエラーが発生します。  
  
```  
"[Microsoft][SQL Server Native Client] Connection is busy with  
results for another hstmt."  
```  
  
## <a name="see-also"></a>参照  
 [ODBC&#41;&#40;の一括コピー操作の実行](performing-bulk-copy-operations-odbc.md)   
 [データ &#40;SQL Server&#41;の一括インポートと一括エクスポート](../import-export/bulk-import-and-export-of-data-sql-server.md)  
  
  
