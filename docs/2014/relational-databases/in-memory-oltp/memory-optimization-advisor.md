---
title: メモリ最適化アドバイザー | Microsoft Docs
ms.custom: ''
ms.date: 10/26/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
f1_keywords:
- sql12.swb.memoryoptimizationwizard.f1
- swb.memoryoptimizationwizard.f1
ms.assetid: 181989c2-9636-415a-bd1d-d304fc920b8a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 1d2fe137a21f2bd48113e65524b4315494f40a49
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "63157999"
---
# <a name="memory-optimization-advisor"></a>メモリ最適化アドバイザー
  トランザクション パフォーマンス レポート ツール ( [Determining if a Table or Stored Procedure Should Be Ported to In-Memory OLTP](determining-if-a-table-or-stored-procedure-should-be-ported-to-in-memory-oltp.md)を参照) では、インメモリ OLTP を使用するように移植した場合に効果が得られる、データベース内のテーブルが通知されます。 インメモリ OLTP を使用するように移植するテーブルを特定した後に、メモリ最適化アドバイザーを使用すると、ディスク ベースのデータベース テーブルをインメモリ OLTP に移行できます。  
  
 まず、ディスク ベースのデータベース テーブルが格納されているインスタンスに接続します。 
  [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] または [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] のインスタンスに接続できます。 ただし、アドバイザーを使用して移行操作を実行する場合は、インメモリ OLTP 機能が有効になっている [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] インスタンスに接続する必要があります。 インメモリ OLTP の要件の詳細については、「 [Requirements for Using Memory-Optimized Tables](memory-optimized-tables.md)」を参照してください。  
  
 移行方法については、「[In-Memory OLTP - Common Workload Patterns and Migration Considerations](https://msdn.microsoft.com/library/dn673538.aspx)」(インメモリ OLTP - 一般的なワークロード パターンと移行に関する考慮事項) を参照してください。  
  
## <a name="walkthrough-using-the-memory-optimization-advisor"></a>メモリ最適化アドバイザーの使用に関するチュートリアル  
 
  **オブジェクト エクスプローラー**で、変換するテーブルを右クリックし、 **[メモリ最適化アドバイザー]** を選択します。 これにより、 **テーブルのメモリ最適化アドバイザー**のようこそページが表示されます。  
  
### <a name="memory-optimization-checklist"></a>メモリ最適化のチェック リスト  
 
  **テーブルのメモリ最適化アドバイザー** のようこそページで **[次へ]** をクリックすると、メモリ最適化のチェック リストが表示されます。 メモリ最適化テーブルでは、ディスク ベース テーブルのすべての機能がサポートされているわけではありません。 メモリ最適化のチェック リストでは、メモリ最適化テーブルと互換性のない機能がディスク ベース テーブルで使用されているかどうかが報告されます。 
  **テーブルのメモリ最適化アドバイザー** では、インメモリ OLTP の使用へ移行できるようにディスク ベース テーブルが変更されるわけではありません。 移行を続行する前に、それらの変更を行う必要があります。 
  **テーブルのメモリ最適化アドバイザー** では、非互換性が検出されるたびに、ディスク ベース テーブルの変更に役立つ情報へのリンクが表示されます。  
  
 移行を計画するために、このような非互換性の一覧を保持する場合は、 **[レポートの生成]** をクリックして HTML の一覧を生成します。  
  
 テーブルで非互換性が検出されず、インメモリ OLTP を使用して [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] インスタンスに接続している場合は、 **[次へ]** をクリックします。  
  
### <a name="memory-optimization-warnings"></a>[メモリ最適化の警告]  
 次の [メモリ最適化の警告] ページには、問題の一覧があります。この一覧にある問題によって、インメモリ OLTP を使用するためのテーブルの移行が妨げられることはありませんが、他のオブジェクト (ストアド プロシージャや CLR 関数など) の動作が失敗したり予期しない動作が発生する可能性があります。  
  
 一覧に表示される最初のいくつかの警告は、情報提供を目的としているため、テーブルに当てはまる場合と当てはまらない場合があります。 テーブルの右側の列にあるリンクをクリックすると、詳細情報が表示されます。  
  
 警告テーブルには、テーブルには存在しない可能性のある警告も表示されます。  
  
 対処可能な警告には、左側の列に黄色い三角形が表示されます。 対処可能な警告がある場合、移行を終了し、警告を解決してから、処理を再開してください。 警告を解決しないと、移行されるテーブルが原因でエラーが発生する可能性があります。  
  
 このような警告の HTML レポートを生成するには、 **[レポートの生成]** をクリックしてください。 
  **[次へ]** をクリックします。  
  
### <a name="review-optimization-options"></a>[最適化オプションの確認]  
 次の画面では、インメモリ OLTP への移行に関するオプションを変更できます。  
  
 [メモリ最適化ファイル グループ]  
 メモリ最適化ファイル グループの名前です。 メモリ最適化テーブルを作成する前に、データベースには、1 つ以上のファイルを含むメモリ最適化ファイル グループを用意しておく必要があります。  
  
 メモリ最適化ファイル グループがない場合は、既定の名前を変更できます。 メモリ最適化ファイル グループを削除することはできません。 メモリ最適化ファイル グループが存在する場合、自動終了やデータベース ミラーリングなどのデータベース レベルの機能の一部が無効になることがあります。  
  
 データベースにメモリ最適化ファイル グループが既に存在する場合、このフィールドにはその名前があらかじめ設定されており、このフィールドの値を変更することはできません。  
  
 [論理ファイル名とファイル パス]  
 メモリ最適化テーブルが格納されるファイルの名前です。 メモリ最適化テーブルを作成する前に、データベースには、1 つ以上のファイルを含むメモリ最適化ファイル グループを用意しておく必要があります。  
  
 既存のメモリ最適化ファイル グループがない場合は、ファイルの既定の名前とパスを変更すると、移行プロセスの終了時に作成できます。  
  
 既存のメモリ最適化ファイル グループがある場合は、これらのフィールドにはあらかじめ値が設定されており、それらの値を変更することはできません。  
  
 [元のテーブル名を変更]  
 移行プロセスの終了時には、テーブルの現在の名前を使用して新しいメモリ最適化テーブルが作成されます。 名前の競合を回避するには、現在のテーブルの名前を変更する必要があります。 その名前は、このフィールドで変更できます。  
  
 [現在の推定メモリ コスト (MB)]  
 メモリ最適化アドバイザーでは、ディスク ベース テーブルのメタデータに基づいて、新しいメモリ最適化テーブルで消費されるメモリの量が推定されます。 テーブル サイズの計算については、「 [メモリ最適化テーブルのテーブルと行のサイズ](table-and-row-size-in-memory-optimized-tables.md)」で説明しています。  
  
 割り当てられているメモリが十分でない場合は、移行プロセスが失敗することがあります。  
  
 [新しいメモリ最適化テーブルにテーブル データもコピーする]  
 新しいメモリ最適化テーブルに現在のテーブルのデータも移動する場合は、このオプションを選択します。 このオプションを選択しないと、新しいメモリ最適化テーブルは作成されますが、行が存在しません。  
  
 [既定でテーブルを持続性のあるテーブルとして移行する]  
 インメモリ OLTP では、持続性のあるメモリ最適化テーブルと比較するとパフォーマンスが優れている持続性のないテーブルがサポートされています。 ただし、持続性のないテーブルのデータはサーバーの再起動時に失われます。  
  
 このオプションを選択した場合、メモリ最適化アドバイザーによって、持続性のあるテーブルではなく持続性のないテーブルが作成されます。  
  
> [!WARNING]  
>  このオプションを選択するのは、持続性のないテーブルと関連したデータ損失のリスクを理解している場合だけにしてください。  
  
 
  **[次へ]** をクリックして、続行します。  
  
### <a name="review-primary-key-conversion"></a>[主キーの変換の確認]  
 次の画面は **[主キーの変換の確認]** です。 メモリ最適化アドバイザーでは、テーブルに 1 つ以上の主キーが存在するかどうかが検出され、主キーのメタデータに基づいて列の一覧が作成されます。 列の一覧が作成されなければ、持続性のあるメモリ最適化テーブルに移行する場合に、主キーを作成する必要があります。  
  
 主キーが存在せず、テーブルを持続性のないテーブルに移行している場合、この画面は表示されません。  
  
 テキスト列 (`char`、`nchar`、`varchar`、および `nvarchar` 型の列) の場合は、適切な照合順序を選択する必要があります。 インメモリ OLTP でサポートされているのは、メモリ最適化テーブルの列の BIN2 照合順序のみで、補助文字を使用した照合順序はサポートされていません。 サポートされている照合順序と、照合順序を変更した場合に考えられる影響については、「 [Collations and Code Pages](../../database-engine/collations-and-code-pages.md) 」を参照してください。  
  
 主キーの構成可能なパラメーターは次のとおりです。  
  
 [この主キーの新しい名前を選択する]  
 このテーブルの主キーの名前は、データベース内で一意である必要があります。 主キーの名前は、ここで変更できます。  
  
 [この主キーの種類を選択する]  
 インメモリ OLTP では、メモリ最適化テーブルで次の 2 種類のインデックスをサポートしています。  
  
-   NONCLUSTERED HASH インデックス。 このインデックスは、多数のポイント参照を含むインデックスに最適です。 
  **[バケット数]** フィールドで、このインデックスのバケット数を構成できます。  
  
-   NONCLUSTERED インデックス。 この種類のインデックスは、多数の範囲クエリを含むインデックスに最適です。 
  **[並べ替え列と並べ替え順序]** の一覧で、各列の並べ替え順序を構成できます。  
  
 主キーに最適なインデックスの種類を理解するには、「 [ハッシュ インデックス](../../database-engine/hash-indexes.md)」を参照してください。  
  
 主キーを選択したら、 **[次へ]** をクリックします。  
  
### <a name="review-index-conversion"></a>[インデックスの変換の確認]  
 次は **[インデックスの変換の確認]** ページです。 メモリ最適化アドバイザーでは、テーブルに 1 つ以上のインデックスが存在するかどうかが検出され、列とデータ型の一覧が作成されます。 
  **[インデックスの変換の確認]** ページで構成できるパラメーターは、前の **[主キーの変換の確認]** ページと同じです。  
  
 主キーのみがあるテーブルを持続性のあるテーブルに移行している場合、この画面は表示されません。  
  
 テーブル内の各インデックスについて変換するかどうかを決定したら、 **[次へ]** をクリックします。  
  
### <a name="verify-migration-actions"></a>[移行アクションの確認]  
 次は **[移行アクションの確認]** ページです。 移行操作のスクリプトを作成するには、 **[スクリプト]** をクリックして [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成します。 その後、スクリプトを変更および実行できます。 テーブルの移行を開始するには、 **[移行]** をクリックします。  
  
 移行プロセスが完了したら、 **オブジェクト エクスプローラー** を更新して、新しいメモリ最適化テーブルと古いディスク ベース テーブルを確認します。 古いテーブルは保持しておくことも、都合のよいときに削除することも可能です。  
  
## <a name="see-also"></a>参照  
 [インメモリ OLTP への移行](migrating-to-in-memory-oltp.md)  
  
  
