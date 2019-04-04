---
title: SQL Server 2016 Analysis Services の新機能新機能 |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 873fd4bc1e010b2f7e2795368f8f209dfee23ea0
ms.sourcegitcommit: 6443f9a281904af93f0f5b78760b1c68901b7b8d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/11/2018
ms.locfileid: "53210191"
---
# <a name="what39s-new-in-analysis-services"></a>Analysis Services の新機能
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

SQL Server 2016 Analysis Services は、各種パフォーマンスの向上、ソリューションの作成を簡単に、データベース管理の自動化を提供する新しい拡張機能で強化されたリレーションシップで双方向クロス フィルタ リング、並列パーティション処理とその他。 このリリースのほとんどの拡張機能の核となるのは、表形式モデル データベースの新しい互換性レベル 1200 です。     

## <a name="azure-analysis-services"></a>Azure Analysis Services
2016 SQL PASS Conference で発表されたように、Azure のサービスとしてクラウドで Analysis Services を使用できるようになりました。 **Azure Analysis Services** 1200 以降の互換性レベル表形式モデルをサポートしています。 DirectQuery、パーティション、行レベルのセキュリティ、双方向のリレーションシップ、および翻訳がすべてサポートされます。 詳細を確認し、無料版をお試しになる場合は、「 [Azure Analysis Services](http://azure.microsoft.com/services/analysis-services/)」を参照してください。 

## <a name="whats-new-in-sql-server-2016-service-pack-1-sp1-analysis-services"></a>SQL Server 2016 Service Pack 1 (SP1) Analysis Services の新機能

[SQL Server 2016 SP1 をダウンロードする](http://www.microsoft.com/download/details.aspx?id=54276) 

SQL Server 2016 Service SP1 Analysis Services は、Non-Uniform Memory Access (NUMA) に対応し、 **Intel Threading Building Blocks** (Intel TBB) に基づいてメモリ割り当てを最適化することで、パフォーマンスとスケーラビリティを改善しています。 この新しい機能で、より少数の強力なエンタープライズ サーバーでより多くのユーザーをサポートできるので、総保有コスト (TCO) を下げることができます。 

特に、SQL Server 2016 SP1 Analysis Services は、以下の主要領域の機能を改善しています。

-   **NUMA 対応** - NUMA のサポートを改善するために、Analysis Services 内のインメモリ (VertiPaq) エンジンは各 NUMA ノードで別のジョブ キューを維持するようになりました。 これによって、セグメント スキャン ジョブを、セグメント データのメモリが割り当てられている同じノードで確実に実行することができます。 ただし、NUMA 対応は、既定で 4 つ以上の NUMA ノードがあるシステムで有効にすることができます。 2 つのノードのシステムでのコストにアクセスするリモート割り当て済みメモリは NUMA の詳細を管理するオーバーヘッドを保証しません。
-   **メモリの割り当て** - Analysis Services は、Intel Threading Building Blocks (Intel TBB) で高速になりました。Intel TBB は、すべてのコアに別のメモリ プールを提供するスケーラブルな割り当てツールです。 コア数の増加に比例してシステムを拡張することができます。
-   **ヒープの断片化** - Intel TBB ベースのスケーラブルな割り当てツールを使用すると、Windows ヒープで発生するヒープの断片化によるパフォーマンスの問題を軽減できます。

パフォーマンスとスケーラビリティのテストでは、大規模なマルチノード エンタープライズ サーバー上で SQL Server 2016 SP1 Analysis Services を実行するときに、クエリ スループットが大幅に向上しました。


## <a name="whats-new-in-sql-server-2016-analysis-services"></a>SQL Server 2016 Analysis Services の新機能新機能

このリリースのほとんどの拡張機能は表形式モデルを対象としていますが、多次元モデルを対象とするものもあります。たとえば、DB2 や Oracle などのデータソースに対する個別のカウント ROLAP の最適化、Excel 2016 のドリルスルーの複数選択のサポート、Excel のクエリの最適化などがあります。    

#### <a name="get-the-latest-tools"></a>最新のツールを入手する
このリリースではすべての機能強化を最大限に活用するために、必ず SSDT および SSMS の最新バージョンをインストールしてください。    
- [SQL Server Data Tools (SSDT) のダウンロード](http://msdn.microsoft.com/library/mt204009.aspx)    
- [SQL Server Management Studio (SSMS) のダウンロード](http://msdn.microsoft.com/library/mt238290.aspx)   

カスタムの AMO 依存アプリケーションがある場合は、AMO の更新バージョンをインストールする必要がある可能性があります。 手順については、「[Analysis Services データ プロバイダー &#40;AMO、ADOMD.NET、MSOLAP&#41; をインストールする](../analysis-services/instances/install-windows/install-analysis-services-data-providers-amo-adomd-net-msolap.md)」を参照してください。    

## <a name="modeling"></a>モデリング    
### <a name="improved-modeling-performance-for-tabular-1200-models"></a>表形式モデル 1200 の強化されたモデリング パフォーマンス    
表形式モデル 1200 では、表形式モデル 1100 や 1103 よりも SSDT のメタデータ操作がより高速です。 同じハードウェア上で比較すると、テーブルを 23 個持つ、SQL Server 2014 の互換性レベル (1103) に設定されたモデルでリレーションシップを作成するのに 3 秒かかるのに対して、互換性レベル 1200 に設定されているモデルで同じリレーションシップを作成するには 1 秒もかかりません。    
### <a name="project-templates-added-for-tabular-1200-models-in-ssdt"></a>SSDT で表形式モデル 1200 に追加されたプロジェクト テンプレート    
このリリースでは、リレーショナルと BI プロジェクトを構築するために、2 つのバージョンの SSDT を使用する必要はなくなりました。 [Visual Studio 2015 用 SQL Server Data Tools](http://msdn.microsoft.com/library/mt204009.aspx) では、互換性レベル 1200 のビルド モデルに使用される **Analysis Services の表形式プロジェクト** を含む、Analysis Services ソリューションのプロジェクト テンプレートを追加します。 多次元およびデータ マイニング ソリューション用のその他の Analysis Services プロジェクト テンプレートも含まれますが、以前のリリース (1100 または 1103) と同じ機能レベルです。    
### <a name="display-folders"></a>表示フォルダー
表形式モデル 1200 で表示フォルダーが使用できるようになりました。 SQL Server Data Tools で定義され、Excel または Power BI Desktop などのクライアント アプリケーションで表示された表示フォルダーでは、より簡単にフィールド リストを移動できるように階層構造を追加し、多くのメジャーを個々のフォルダーに整理できます。
### <a name="bi-directional-cross-filtering"></a>双方向のクロス フィルター処理
このリリースでは、表形式モデルで双方向のクロス フィルターを有効にするための組み込みアプローチが新たに導入されています。これにより、テーブル リレーションシップ間でフィルター コンテキストを伝達するために DAX 式を手動で作成する必要がなくなります。 フィルターは、方向を高い確実性で確立できた場合にのみ自動生成されます。 テーブル リレーションシップで複数のクエリ パスの形式にあいまいさがある場合、フィルターは自動的に作成されません。 詳細については、「 [SQL Server 2016 Analysis Services における表形式モデルの双方向のクロス フィルター](../analysis-services/tabular-models/bi-directional-cross-filters-tabular-models-analysis-services.md) 」を参照してください。
 ### <a name="translations"></a>翻訳    
 翻訳されたメタデータを表形式モデル 1200 に保存できるようになりました。 モデル内のメタデータには、 **Culture**のフィールド、翻訳されたキャプション、および翻訳された説明が含まれます。 翻訳を追加するには、[!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で **[モデル]** > **[翻訳]** の順にコマンドを使用します。 詳細については、「[表形式モデルでの翻訳 &#40;Analysis Services&#41;](../analysis-services/tabular-models/translations-in-tabular-models-analysis-services.md)」を参照してください。    
 ### <a name="pasted-tables"></a>貼り付けられたテーブル    
 モデルに貼り付けられたテーブルが含まれる場合、表形式モデルを 1100 または 1103 から 1200 にアップグレードできるようになりました。 [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]を使用することをお勧めします。 SSDT では、 **CompatibilityLevel** を 1200 に設定して、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスに展開します。 詳細については、「 [Compatibility Level for Tabular models in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md) 」を参照してください。    
 ### <a name="calculated-tables-in-ssdt"></a>SSDT の計算テーブル    
*計算テーブル* は、SSDT での DAX 式またはクエリに基づいたモデルのみの構築です。 データベースに展開すると、計算テーブルを通常のテーブルと区別することはできません。    

 計算テーブルには、特定のロールの既存のテーブルを公開するために新しいテーブルを作成するなど、いくつかの使用法があります。 その典型例は、複数のコンテキスト (注文日、出荷日など) で動作する Date テーブルです。 任意のロールの計算テーブルを作成することによって、計算テーブルを使用してクエリまたはデータ操作を容易にするために、テーブル リレーションシップをアクティブにできるようになりました。 計算テーブルの別の使用法は、モデルにのみ存在するまったく新しいテーブルに、既存のテーブルの部品を結合することです。  参照してください[計算テーブルを作成する](../analysis-services/tabular-models/create-a-calculated-table-ssas-tabular.md)詳細。    
 ### <a name="formula-fixup"></a>数式の修正    
 表形式モデル 1200 で数式を修正すると、SSDT は名前が変更された列または名前を参照しているすべてのメジャーを自動更新します。    
 ### <a name="support-for-visual-studio-configuration-manager"></a>Visual Studio 構成マネージャーのサポート    
 テスト環境や実稼働前環境などの複数の環境をサポートするために、Visual Studio では、開発者が構成マネージャーを使用して、複数のプロジェクト構成を作成できるようにします。 多次元モデルでは既にこれを利用していますが、表形式モデルでは利用していませんでした。 このリリースでは、構成マネージャーを使用して、異なるサーバーに展開できるようになりました。    

## <a name="instance-management"></a>インスタンス管理    
 ### <a name="administer-tabular-1200-models-in-ssms"></a>SSMS での表形式モデル 1200 の管理    
 このリリースでは、表形式サーバー モードの Analysis Services インスタンスが、表形式モデルを任意の互換性レベル (1100、1103、1200) で実行できます。 最新の [SQL Server Management Studio](http://msdn.microsoft.com/library/mt238290.aspx) は、プロパティを表示し、互換性レベル 1200 の表形式モデルのデータベース モデル管理を提供するように更新されています。    
 ### <a name="parallel-processing-for-multiple-table-partitions-in-tabular-models"></a>表形式モデルでの複数のテーブル パーティションの並列処理    
 このリリースには、処理パフォーマンスを強化する、2 つ以上のパーティションを持つテーブルへの新しい並行処理機能が含まれます。 この機能には、構成設定はありません。 パーティションを構成して、テーブルの処理の詳細については、[テーブル モデル パーティション](../analysis-services/tabular-models/tabular-model-partitions-ssas-tabular.md)を参照してください。    
 ### <a name="add-computer-accounts-as-administrators-in-ssms"></a>SSMS の管理者としてコンピューター アカウントを追加する    
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 管理者は、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] を使用して、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 管理者グループのメンバーにするコンピューター アカウントを構成できるようになりました。 **[ユーザーまたはグループの選択]** ダイアログ ボックスで、コンピューター ドメインの **[場所]** を設定して、 **[コンピューター]** のオブジェクトの種類を追加します。 詳細については、「 [Analysis Services インスタンスにサーバー管理者権限を付与する](../analysis-services/instances/grant-server-admin-rights-to-an-analysis-services-instance.md)」を参照してください。    
 ### <a name="dbcc-for-analysis-services"></a>Analysis Services 用 DBCC    
 Database Consistency Checker (DBCC) は、データベースの読み込みで潜在的なデータ破損の問題を検出するために内部的に実行されますが、自分のデータまたはモデルに問題があると考えられる場合は、オンデマンドで実行することもできます。 DBCC は、モデルが表形式か多次元かに応じて異なるチェックを実行します。 詳細については、「[Analysis Services の表形式および多次元データベース用 Database Consistency Checker &#40;DBCC&#41;](../analysis-services/instances/database-consistency-checker-dbcc-for-analysis-services.md)」を参照してください。    
 ### <a name="extended-events-updates"></a>拡張イベントの更新プログラム    
 このリリースでは、グラフィカル ユーザー インターフェイスを [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] に追加し、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の拡張イベントを構成および管理します。 ライブ データ ストリームを設定して、リアルタイムでサーバー アクティビティを監視したり、より高速に分析するためにセッション データをメモリに継続して読み込まれるようにしたり、オフライン分析用にデータ ストリームをファイルで保存したりすることができます。 詳細については、「 [SQL Server 拡張イベントを使用した Analysis Services の監視](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md) 」と「 [Analysis Services で拡張イベントを使用する (Guy in a Cube のブログ投稿とビデオ)](http://blogs.msdn.com/b/analysisservices/archive/2015/09/22/using-extended-events-with-sql-server-analysis-services-2016-cpt-2-3.aspx)」を参照してください。    



## <a name="scripting"></a>スクリプトの作成
 ### <a name="powershell-for-tabular-models"></a>表形式モデル用の PowerShell    
 このリリースには、互換性レベル 1200 の表形式モデル用の PowerShell の拡張機能が含まれています。 すべての該当するコマンドレットは、に加えて、表形式モードに固有のコマンドレットを使用できます。[Invoke-processasdatabase](../analysis-services/powershell/invoke-processasdatabase.md)と[Invoke ProcessTable コマンドレット](../analysis-services/powershell/invoke-processtable-cmdlet.md)します。    
 ### <a name="ssms-scripting-database-operations"></a>SSMS スクリプトのデータベース操作    
 [最新の SQL Management Studio (SSMS)](http://msdn.microsoft.com/library/mt238290.aspx)では、スクリプトで Create、Alter、Delete、Backup、Restore、Attach、Detach などのデータベース コマンドを使用できるようになりました。 Output は、JSON での表形式モデルのスクリプト言語 (TMSL) です。 詳細については、「[表形式モデルのスクリプト言語 &#40;TMSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)」を参照してください。    
 ### <a name="analysis-services-execute-ddl-task"></a>Analysis Services DDL 実行タスク    
 [Analysis Services DDL 実行タスク](../integration-services/control-flow/analysis-services-execute-ddl-task.md) は、表形式モデルのスクリプト言語 (TMSL) コマンドも受け入れられるようになりました。     
 ### <a name="ssas-powershell-cmdlet"></a>SSAS PowerShell コマンドレット    
 SSAS PowerShell コマンドレット **Invoke-ASCmd** は、表形式モデルのスクリプト言語 (TMSL) コマンドを受け入れるようになりました。 その他の SSAS PowerShell コマンドレットは、新しい表形式のメタデータを使用するために、今後のリリースで更新される可能性があります (例外はリリース ノートに記載されます)。    
詳細については、「 [Analysis Services PowerShell Reference](../analysis-services/powershell/analysis-services-powershell-reference.md) 」を参照してください。    
 ### <a name="tabular-model-scripting-language-tmsl-supported-in-ssms"></a>SSMS でサポートされる表形式モデルのスクリプト言語 (TMSL)    
  [最新バージョンの SSMS](http://msdn.microsoft.com/library/mt238290.aspx)を使用して、表形式モデル 1200 のほとんどの管理タスクを自動化するスクリプトを作成できるようになりました。 現時点では、次のタスクをスクリプト化できます。プロセス レベル、および CREATE、ALTER、データベース レベルで削除します。    
    
 機能的には、TMSL は、表形式のメタデータを説明する **model**、 **table**、および **relationship** などのネイティブ記述子を使用する TMSL を除いて、多次元オブジェクトの定義を提供する XMLA ASSL の拡張機能と同じです。 スキーマの詳細については、「[表形式モデルのスクリプト言語 &#40;TMSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)」を参照してください。    
    
 表形式モデル用に作成された JSON ベースのスクリプトは、次のようになります。    
    
```    
{    
  "create": {    
    "database": { 
      "name": "AdventureWorksTabular1200",    
      "id": "AdventureWorksTabular1200",    
      "compatibilityLevel": 1200,    
      "readWriteMode": "readWrite",    
      "model": {}    
    }    
  }    
}    
```    

ペイロードは、上述の例のように最小限に抑えた、または完全なセットのオブジェクト定義で高水準に装飾された JSON ドキュメントです。 構文については、「[表形式モデルのスクリプト言語 &#40;TMSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)」で説明しています。

データベース レベルで、CREATE、ALTER、および DELETE コマンドは、TMSL スクリプトを使い慣れた XMLA ウィンドウに出力します。  Process などの他のコマンドは、このリリースでもスクリプトを作成できます。 将来のリリースで、その他の多くのアクションに対するスクリプトのサポートが追加される可能性があります。    

**スクリプト可能なコマンド** | **[説明]**
--------------- | ----------------
作成|データベース、接続、またはパーティションを追加します。 ASSL では CREATE に相当します。
createOrReplace|以前のバージョンを上書きして、既存のオブジェクト定義 (データベース、接続、またはパーティション) を更新します。 ASSL では、AllowOverwrite が true、および ObjectDefinition が ExpandFull に設定された ALTER に相当します。
delete|オブジェクトの定義を削除します。 ASSL では DELETE に相当します。
refresh|オブジェクトを処理します。 ASSL では PROCESS に相当します。

## <a name="dax"></a>DAX
### <a name="improved-dax-formula-editing"></a>強化された DAX 数式の編集
数式バーの更新プログラムでは、関数、フィールド、および構文の色を区別して、より簡単に数式を記述することができます。これは、インテリジェント関数やフィールドの候補を提供し、DAX 式に間違っている部分がある場合はエラーの *波線*を使用して示します。 複数の行 (Alt + Enter) とインデント (Tab) も使用できます。 数式バーもできるようになりました、メジャーの一部としてコメントを作成、入力するだけにする"//"と同じ行にこれらの文字がコメントを考慮する後のすべて。

### <a name="dax-variables"></a>DAX の変数    
このリリースでは、DAX の変数のサポートが追加されました。 変数は、式の結果を名前付きの変数として保存できるようになりました。これは、他のメジャーの式に引数として渡すことができます。 結果の値が可変式に対して計算されると、その変数が別の式で参照される場合でも、それらの値は変更されません。 詳細については、「 [VAR 関数](http://msdn.microsoft.com/library/mt243785.aspx)」を参照してください。    
### <a name="new-dax-functions"></a>DAX の新しい関数
このリリースでは、計算を高速化し、Power BI での視覚化機能を強化する 50 以上の新しい関数が DAX に導入されました。 詳細については、「 [New DAX Functions](http://msdn.microsoft.com/library/mt704075.aspx)」 (DAX の新しい関数) を参照してください。
### <a name="save-incomplete-measures"></a>不完全なメジャーを保存する
不完全な DAX メジャーを表形式 1200 のモデル プロジェクトに直接保存できるようになりました。作業を続ける準備ができたときに、もう一度選択することができます。
### <a name="additional-dax-enhancements"></a>DAX の追加の拡張機能
- 空以外の計算 - 空以外で必要なスキャンの数を減らします。
- メジャー フュージョン - 同じテーブルからの複数のメジャーは単一のストレージ エンジン クエリに結合されます。
- グループ化セット - クエリがメジャーを複数の粒度 (合計/年/月) で問い合わせるとき、単一のクエリは最低レベルで送信され、残りの粒度は最低レベルから派生します。     
- 冗長な結合の排除 - ストレージ エンジンに対する単一のクエリがディメンション列とメジャー値の両方を返します。
- IF/SWITCH の厳密な評価 - 条件が false の分岐の結果がストレージ エンジンのクエリになりません。 以前は分岐が積極的に評価されていましたが、後に結果は破棄されていました。     
    
## <a name="developer"></a>Developer    
 ### <a name="microsoftanalysisservicestabular-namespace-for-tabular-1200-programmability-in-amo"></a>AMO 内の表形式 1200 のプログラミングの Microsoft.AnalysisServices.Tabular 名前空間
 Analysis Services 管理オブジェクト (AMO) は、プログラムを使用した表形式 1200 モデルの作成や変更用にデータ定義言語を提供するためだけでなく、SQL Server 2016 Analysis Services の表形式モード インスタンスの管理用に新しい表形式の名前空間を含めるために更新されます。 API の詳細については、「 [Microsoft.AnalysisServices.Tabular](http://msdn.microsoft.com/library/microsoft.analysisservices.tabular.aspx) 」を参照してください。    
 ### <a name="analysis-services-management-objects-amo-updates"></a>Analysis Services 管理オブジェクト (AMO) の更新プログラム
 [Analysis Services Management Objects &#40;AMO&#41;](http://msdn.microsoft.com/library/mt436122.aspx) は、2 つ目のアセンブリ (Microsoft.AnalysisServices.Core.dll) を含めるためにリファクタリングされています。 新しいアセンブリでは、サーバー モードに関係なく、Analysis Services に広範なアプリケーションを持つサーバー、データベース、およびロールなどの共通クラスを分離させます。    
    
 以前は、これらのクラスは元の Microsoft.AnalysisServices アセンブリの一部でした。 これらのクラスを新しいアセンブリに移動することで、ジェネリック API とコンテキスト固有の API が明確に区別され、AMO への今後の拡張機能の下準備となります。    
    
 既存のアプリケーションは、新しいアセンブリの影響を受けることはありません。 ただし、何らかの理由で新しい AMO アセンブリを使用してアプリケーションを再構築する場合は、必ず Microsoft.AnalysisServices.Core に参照を追加してください。    
    
 同様に、AMO に読み込まれたり、呼び出されたりする PowerShell スクリプトは、Microsoft.AnalysisServices.Core.dll を読み込む必要があります。 任意のスクリプトを更新してください。  

### <a name="json-editor-for-bim-files"></a>BIM ファイル用の JSON エディター
Visual Studio 2015 の [コードの表示] で、表形式モデル 1200 の BIM ファイルを JSON 形式で表示するようになりました。 Visual Studio のバージョンによって、組み込み JSON エディターを使用した JSON 形式、または単純なテキストのどちらで、BIM ファイルを表示するかを決定します。

モデルのセクションの展開/折りたたみ機能と共に JSON エディターを使用するには、最新バージョンの SQL Server Data Tools と Visual Studio 2015 (無料の Community Edition を含むすべてのエディション) が必要になります。 SSDT のその他すべてのバージョンまたは Visual Studio では、BIM ファイルは単純なテキストとして JSON 形式で表示されます。
少なくとも、空のモデルには、次の JSON が含まれます。

    ```    
    {    
      "name": "SemanticModel",
      "id": "SemanticModel",
      "compatibilityLevel": 1200,
      "readWriteMode": "readWrite",
      "model": {}
    }    
    ```    
    
> [!WARNING]
> JSON を直接編集しないでください。 編集すると、モデルが破壊される場合があります。    
>  ### <a name="new-elements-in-ms-csdlbi-20-schema"></a>MS-CSDLBI 2.0 スキーマの新しい要素    
>  次の要素が、[MS-CSDLBI] 2.0 スキーマで定義された **TProperty** 複合型に追加されました。    
    
|要素|定義|    
|-------------|----------------|    
|DefaultValue|クエリを評価するときに使用される値を指定するプロパティ。 DefaultValue プロパティはオプションですが、メンバーから値を集計できない場合は、自動的に選択されます。|    
|統計|列に関連付けられている基になるデータからの統計情報のセット。 「ビジネス インテリジェンス注釈付きの概念スキーマ定義ファイル形式」ドキュメントのセクション 2.1.13.5 で説明されているように、これらの統計情報は TPropertyStatistics 複合型で定義され、生成するには計算コストが高い場合にのみ提供されます。|    
    
## <a name="directquery"></a>DirectQuery    
### <a name="new-directquery-implementation"></a>新しい DirectQuery の実装    
このリリースでは、表形式 1200 モデルの DirectQuery の拡張機能が大幅に改善されています。 概要を次に示します。    
-   DirectQuery ではパフォーマンスを向上させるより単純なクエリを生成するようになりました。    
-   モデル デザインとテストに使用されるサンプル データセットの定義をより管理できるようになりました。    
-   DirectQuery モードの表形式 1200 モデルで行レベルのセキュリティ (RLS) がサポートされるようになりました。 以前は、RLS が存在することで、DirectQuery モードで表形式モデルを配置できませんでした。    
-   DirectQuery モードの表形式 1200 モデルで計算列がサポートされるようになりました。 以前は、計算列が存在することで、DirectQuery モードで表形式モデルが配置されることを回避していました。    
-   VertiPaq および DirectQuery の冗長な結合の除去など、パフォーマンスが最適化されました。 

### <a name="new-data-sources-for-directquery-mode"></a>DirectQuery モードの新しいデータ ソース    
 これで、DirectQuery モードで表形式モデル 1200 のサポートされるデータ ソースには、Oracle、Teradata および Microsoft Analytics Platform (以前は並列データ ウェアハウスと呼ばれます) が含まれます。    
    
詳細についてを参照してください。 [DirectQuery モード](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)します。    

## <a name="see-also"></a>参照
[Analysis Services チーム ブログ](http://blogs.msdn.microsoft.com/analysisservices/)    
[SQL Server 2016 の新機能](../sql-server/what-s-new-in-sql-server-2016.md)    
     

