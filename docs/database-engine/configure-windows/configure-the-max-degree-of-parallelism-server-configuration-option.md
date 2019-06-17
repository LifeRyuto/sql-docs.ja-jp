---
title: max degree of parallelism サーバー構成オプションの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/02/2017
ms.prod: sql
ms.prod_service: high-availability
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- parallel queries [SQL Server]
- processors [SQL Server], parallel queries
- number of processors for parallel queries
- max degree of parallelism option
- MaxDop
ms.assetid: 86b65bf1-a6a1-4670-afc0-cdfad1558032
author: MikeRayMSFT
ms.author: mikeray
manager: jroth
ms.openlocfilehash: 0e8faaeb6a809caf5bd8c42ceee94cbbb0702979
ms.sourcegitcommit: ad2e98972a0e739c0fd2038ef4a030265f0ee788
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/07/2019
ms.locfileid: "66794143"
---
# <a name="configure-the-max-degree-of-parallelism-server-configuration-option"></a>max degree of parallelism サーバー構成オプションの構成
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

  このトピックでは、 **または** を使用して、 [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] の [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] max degree of parallelism (MAXDOP) [!INCLUDE[tsql](../../includes/tsql-md.md)]サーバー構成オプションを構成する方法について説明します。 複数のマイクロプロセッサまたは CPU が搭載されているコンピューター上で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスを実行するときは、並列処理の最適な程度、つまり各並列プラン実行で 1 つのステートメントを実行するために使用するプロセッサの数が検出されます。 **max degree of parallelism** オプションを使用すると、並列プラン実行で使用するプロセッサの数を制限できます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、クエリ、インデックス データ定義言語 (DDL) の操作、並列挿入、オンライン列変更、並行統計コレクション、静的およびキーセット ドリブン カーソルの作成の場合に並列実行プランを検討します。

##  <a name="BeforeYouBegin"></a> はじめに  
  
###  <a name="Restrictions"></a> 制限事項と制約事項  
  
-   affinity mask オプションを既定値に設定していないと、対称型多重処理 (SMP) システムで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できるプロセッサの数が制限されることがあります。  
  
###  <a name="Recommendations"></a> 推奨事項  
  
-   このオプションは詳細設定オプションであるため、熟練したデータベース管理者または認定された [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロフェッショナルだけが変更するようにしてください。  
  
-   サーバーで並列処理の最大限度を特定できるようにするには、このオプションを 0 (既定値) に設定します。 並列処理の最大限度を 0 に設定すると、使用可能なすべてのプロセッサ (最大 64 プロセッサ) を [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が使用できます。 並列プランが生成されないようにするには、 **max degree of parallelism** を 1 に設定します。 1 つのクエリ実行で使用できるプロセッサ コアの最大数を指定するには、値を 1 ～ 32,767 に設定します。 使用可能なプロセッサ数よりも多い値を指定すると、実際に使用可能なプロセッサ数が使用されます。 コンピューターにプロセッサが 1 つしか搭載されていない場合、 **max degree of parallelism** の値は無視されます。  
  
-   クエリ ステートメントに MAXDOP クエリ ヒントを指定して、クエリの max degree of parallelism 値をオーバーライドできます。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
-   インデックスを作成または再構築したり、クラスター化インデックスを削除するインデックス操作には、リソースを集中して使用するものがあります。 インデックス ステートメントの MAXDOP インデックス オプションを指定して、インデックス操作の max degree of parallelism 値をオーバーライドできます。 MAXDOP 値は実行時にステートメントに適用され、インデックス メタデータには保存されません。 詳細については、「 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)」を参照してください。  
  
-   クエリおよびインデックスの操作だけでなく、このオプションも DBCC CHECKTABLE、DBCC CHECKDB、および DBCC CHECKFILEGROUP の並列処理を制御します。 トレース フラグ 2528 を使用して、これらのステートメントの並列実行プランを無効にすることができます。 詳細については、「[トレース フラグ &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-traceon-trace-flags-transact-sql.md)」を参照してください。

###  <a name="Guidelines"></a> ガイドライン  
[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降では、サービスの開始中、[!INCLUDE[ssde_md](../../includes/ssde_md.md)]の起動時に NUMA ノードまたはソケットあたり 8 個を超える物理コアが検出されると、既定でソフト NUMA ノードが自動的に作成されます。 [!INCLUDE[ssde_md](../../includes/ssde_md.md)]により、同じ物理コアからさまざまなソフト NUMA ノードに論理プロセッサが配置されます。 次の表に示す推奨事項は、並列クエリのすべてのワーカー スレッドを同じソフト NUMA ノード内に保持することを目的としています。 これにより、ワークロードの NUMA ノード間でクエリのパフォーマンスとワーカー スレッドの分布が向上します。 詳細については、「[ソフト NUMA](../../database-engine/configure-windows/soft-numa-sql-server.md)」を参照してください。

[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降では、**max degree of parallelism** サーバーの構成値を構成する場合、以下のガイドラインを使用します。

||||
|----------------|-----------------|-----------------|
|単一の NUMA ノードを持つサーバー|8 以下の論理プロセッサ|MAXDOP を論理プロセッサ数以下に保つ|
|単一の NUMA ノードを持つサーバー|8 を超える論理プロセッサ|MAXDOP を 8 に保つ|
|複数の NUMA ノードを持つサーバー|NUMA ノードあたり 16 以下の論理プロセッサ|MAXDOP を NUMA ノードあたりの論理プロセッサ数以下に保つ|
|複数の NUMA ノードを持つサーバー|NUMA ノードあたり 16 を超える論理プロセッサ|最大値を 16 として、MAXDOP を NUMA ノードあたりの論理プロセッサ数の半分に保つ|
  
> [!NOTE]
> 上の表の NUMA ノードは、[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] 以降で自動的に作成されたソフト NUMA ノードを表します。   
>  リソース ガバナー ワークロード グループに対して max degree of parallelism オプションを設定する場合は、これらと同じガイドラインを使用します。 詳細については、「[CREATE WORKLOAD GROUP (Transact-SQL)](../../t-sql/statements/create-workload-group-transact-sql.md)」を参照してください。
  
[!INCLUDE[ssKatmai](../../includes/ssKatmai-md.md)] から [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] では、**max degree of parallelism** サーバーの構成値を構成する場合、以下のガイドラインを使用します。

||||
|----------------|-----------------|-----------------|
|単一の NUMA ノードを持つサーバー|8 以下の論理プロセッサ|MAXDOP を論理プロセッサ数以下に保つ|
|単一の NUMA ノードを持つサーバー|8 を超える論理プロセッサ|MAXDOP を 8 に保つ|
|複数の NUMA ノードを持つサーバー|NUMA ノードあたり 8 以下の論理プロセッサ|MAXDOP を NUMA ノードあたりの論理プロセッサ数以下に保つ|
|複数の NUMA ノードを持つサーバー|NUMA ノードあたり 8 を超える論理プロセッサ|MAXDOP を 8 に保つ|
  
###  <a name="Security"></a> セキュリティ  
  
####  <a name="Permissions"></a> Permissions  
 パラメーターなしで、または最初のパラメーターだけを指定して **sp_configure** を実行する権限は、既定ですべてのユーザーに付与されます。 両方のパラメーターを指定して **sp_configure** を実行し構成オプションを変更したり RECONFIGURE ステートメントを実行したりするには、ALTER SETTINGS サーバーレベル権限がユーザーに付与されている必要があります。 ALTER SETTINGS 権限は、 **sysadmin** 固定サーバー ロールと **serveradmin** 固定サーバー ロールでは暗黙のうちに付与されています。  
  
##  <a name="SSMSProcedure"></a> SQL Server Management Studio の使用  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>max degree of parallelism オプションを構成するには  
  
1.  **オブジェクト エクスプローラー**で、サーバーを右クリックし、 **[プロパティ]** をクリックします。  
  
2.  **[詳細設定]** ノードをクリックします。  
  
3.  **[並列処理の最大限度]** ボックスで、並列プランの実行で使用するプロセッサの最大数を指定します。  
  
##  <a name="TsqlProcedure"></a> Transact-SQL の使用  
  
#### <a name="to-configure-the-max-degree-of-parallelism-option"></a>max degree of parallelism オプションを構成するには  
  
1.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]に接続します。  
  
2.  [標準] ツール バーの **[新しいクエリ]** をクリックします。  
  
3.  次の例をコピーしてクエリ ウィンドウに貼り付け、**[実行]** をクリックします。 この例では、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md) を使用して、 `max degree of parallelism` オプションを `8`に設定する方法を示します。  
  
```sql  
USE AdventureWorks2012 ;  
GO   
EXEC sp_configure 'show advanced options', 1;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
EXEC sp_configure 'max degree of parallelism', 16;  
GO  
RECONFIGURE WITH OVERRIDE;  
GO  
```  
  
 詳細については、「 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md)」を参照してください。  
  
##  <a name="FollowUp"></a>補足情報: max degree of parallelism オプションを構成した後  
 新しい設定は、サーバーを再起動しなくてもすぐに有効になります。  
  
## <a name="see-also"></a>参照  
 [affinity mask サーバー構成オプション](../../database-engine/configure-windows/affinity-mask-server-configuration-option.md)   
 [RECONFIGURE &#40;Transact-SQL&#41;](../../t-sql/language-elements/reconfigure-transact-sql.md)   
 [サーバー構成オプション &#40;SQL Server&#41;](../../database-engine/configure-windows/server-configuration-options-sql-server.md) [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)   
 [CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)   
 [ALTER INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/alter-index-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [DBCC CHECKTABLE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checktable-transact-sql.md)   
 [DBCC CHECKDB &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)   
 [DBCC CHECKFILEGROUP &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkfilegroup-transact-sql.md)   
 [並列インデックス操作の構成](../../relational-databases/indexes/configure-parallel-index-operations.md)   
 [クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md) [インデックス オプションの設定](../../relational-databases/indexes/set-index-options.md)  
 [SQL Server の "max degree of parallelism" 構成オプションの推奨事項とガイドライン](https://support.microsoft.com/help/2806535)
  
  
